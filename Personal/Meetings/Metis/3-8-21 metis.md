# Metis Notes for Monday, March 8th
`LINKS:` [[metis week 10]]
`TAGS:` #meeting/career

---
## Lecture - [[PySpark]]
[[Spark]] has ways to integrate with [[Python]] which is cool. We have to start our session in spark.

```python
import pyspark

spark = pyspark.sql.SparkSession.builder.getOrCreate()
```

Now we can pass in some documents to look at. 

```python
documents = ['This is a document',
             'This is another document',
             'This is yet a third document',
             'When will this list of document end',
             'This is the last document']
```

We put these documents into spark using the following code.

```python
doc_df = spark.createDataFrame([(d,) for d in documents], ['word'])
```

There are a few functions that we can use in this process. We can use `col`, `lower`, `split`, and `explode`. 

```python
from pyspark.sql.functions import col, lower, split, explode
```

If we wanted to split the documents into their component words, we can use `split`. This code will lowercase everything and split it into words, then show the documents in full. 

```python
doc_df.withColumn('word',
				  split(lower(col('word')), '\s')) \
	  .show(10, truncate=False)
```

If we want to explode all the documents into one word per document, we can use `explode`. 

```python
doc_df.withColumn('word', 
                  explode(split(lower(col('word')), "\s"))) \
      .show(10, truncate=False)
```

What if we want to count the number of times a give word shows up across all the documents?

```python
doc_df.withColumn('word', 
                  explode(split(lower(col('word')), "\s"))) \
      .where('word != ""') \
      .groupBy('word') \
      .count() \
      .orderBy('count', ascending=False) \
      .show()
```

This above code will output...

```
+--------+-----+
|    word|count|
+--------+-----+
|document|    5|
|    this|    5|
|      is|    4|
|       a|    2|
|   third|    1|
|    will|    1|
|     end|    1|
|      of|    1|
| another|    1|
|     yet|    1|
|     the|    1|
|    list|    1|
|    when|    1|
|    last|    1|
+--------+-----+
```

Whereas in word vectorization, we generate a [[scalars and vectors|vector]] that describes how frequently a word shows up in all the different documents. Here, we're just getting a total sum of all the times the word appears, not broken down by document.

## Lecture - intro to [[Dask]]
Dask should be familiar to [[PySpark]] and to [[distributed file system]] in general. We should turn to dask when we find ourselves in the middleground between the huge amounts of [[data]] that pyspark is good for, and stuff that's still to big for our computer to load into RAM all at once. 

Dask look similar to [[Pandas]] which is really nice. It works on one partition at a time, storing the active piece in RAM and the rest on the local hard drive. Unlike Pandas, dask uses *[[lazy evaluation]],* which is one reason it's more efficient. 

[[lazy evaluation]] is the process of looking at the whole command before work begins. Then, dask finds the ideal order to execute commands in to save time and space. 

Behind the scenes, dask integrates with [[NumPy]]. It manages parallelization in clusters that allow for streaming data. This means that Dask can do parallelized [[machine learning]], referred to as DaskML. 

Basically, its best for extending the workable data size from your RAM to your disk size. It optimizes calculations using lazy evaluation and DAGs. 

See my notebook `hands_on_dask.ipynb` in `onl_ds5/curriculum/propject-05/dask`

We have to set up a client for the session. This determines the amount of computer power we're giving the program.

```python
import dask
import sklearn
import dask.dataframe as dd
import numpy as np
from dask.distributed import Client, progress

client = Client(n_workers=4,
			    threads_per_worker=2,
			    memory_limit='2GB')
```

Let's read in some wine data to work with. 

```python
path = "http://archive.ics.uci.edu/ml/machine-learning-databases/wine-quality/winequality-white.csv"
df = dd.read_csv(path,  # This could also be a url to *stream* from
                 sep=';',
                 blocksize=1e4)  # this is relatively small, for the purposes of demo

```

If we want to see the number of partitions we've broken the data into, we can use `df.npartitions`. In our case, we have 27 partitions. Since we're not using that much data, it makes sense for us to just tell dask to keep all the partitions in RAM at once. So we can tell dask `df = df.persist()` to say that we want to do this.

Now let's do some EDA on this data. We can do the same sorts of stuff that we would do in Pandas. Here are some examples of things we could do. 

```python
df['fixed acidity'].mean()
> dd.Scalar<series-..., dtype=float64> # output

df['fixed acidity'].mean().compute() # this will actually show the answer
> 6.854787668436097 # output
```

Basically after we want a command to execute, we have to pass `.compute()` to tell dask to actually do it. This is a symptom of the lazy computing thing dask is doing. 

## Using [[Dask]] for [[machine learning]]

Dask has its own versions of the models we're familiar with. 

```python
from dask_ml.linear_model import LinearRegression
from dask_ml.model_selection import train_test_split

# get the data
df = dd.read_csv("./data/census_data.csv", header=None)
df.columns =['age','workclass','fnlwght','education','education_num', 
			 'marital_status','occupation',
            'priv_house_serv','race','gender','capital_gain',
			 'capital_loss','hours_per_week',
              'native_country','income']

# for this exercise, we'll use a truncated version of the data
df = df[['age','education','race','gender','capital_gain',
		 'capital_loss','hours_per_week','income']]

# split the data
x = df[['age','education','race','gender','capital_gain','capital_loss','income']]
y = df['hours_per_week']

x_train, x_test, y_train, y_test = train_test_split(x,y, test_size = 0.2, shuffle=True)

# create and fit the lin reg
lr = LinearRegression()
lr.fit(x_train.values, y_train.values)

# etc......
```


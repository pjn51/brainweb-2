# PySpark Documentation
`LINKS:` [source](https://spark.apache.org/docs/latest/api/python/getting_started/quickstart.html)
#article 

---
> [!info]
> This information is from the PySpark documentation's tutorial. 
# Quickstart
This is a short introduction to PySpark given in the documentation. PySpark DataFrames are lazily evaluated and implemented on top of RDDs (resilient distributed datasets). Computation only starts when actions like `collect()` are called. 

PySpark applications start by initializing a `SparkSession`. Below we see how to initialize such a session and prepare it for reading [[SQL]] data.

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.get0rCreate()
```

## DataFrame creation
We can create a PySpark DataFrame from a variety of inputs. We could use a list of lists, tuples, dictionaries, or `pyspark.sql.Row` objects. We can also use a [[Pandas]] DataFrame, and an RDD consisting of such a list.

Below we see an example of creating a PySpark DataFrame from a list of rows:

```python
from datetime import date
import pandas as pd
from pyspark.sql import Row

df = spark.createDataFrame([
	Row(a=1, b=2.1, c='abc',d=date(2000,1,1)),
	Row(a=2, b=4.5, c='def',d=date(2000,1,2)),
	Row(a=3, b=6.6, c='ghi',d=date(2000,1,3))
])
```

We can also pass `schema` to the dataframe, setting a deliberate structure to the accepted [[data]] types per column:

```python
from datetime import date
from pyspark.sql import Row

df = spark.createDataFrame([
	Row(a=1, b=2.1, c='abc',d=date(2000,1,1)),
	Row(a=2, b=4.5, c='def',d=date(2000,1,2)),
	Row(a=3, b=6.6, c='ghi',d=date(2000,1,3))
], schema = 'a long, b double, c string, d date')
```

Here's an example of creating a PySpark DataFrame from a Pandas DataFrame:

```python
import pandas as pd

pandas_df = pd.DataFrame({
	'a': [1,2,3]
	'b': [4.1, 5.1, 6.1]
	'c': ['string', 'yarn', 'thread']
})

spark_df = spark.createDataFrame(pandas_df)
```

## Viewing data
We can call `df.show(n)` to show the first `n` rows of a PySpark DataFrame. `.show()` is an action, and causes PySpark to execute code according to [[lazy evaluation]]. Alternatively, we can enable "eager evaluation" for PySpark DataFrames. This will allow us to perform evaluations immediately rather than go by [[lazy evaluation]] protocol. This can enable us to work piecemeal in [[Jupyter Notebook]]. 

## Selecting and accessing data
Because of lazy evaluation, we cannot simply select the column alone. We can of course call `df.a` to select column `a`, but this will just return `Column<b 'a'>` instead of showing us the data.

If we want to really get the data within column `a`, we must call `df.select(df.a).show()`. This command tells PySpark to select the A column, and then show the data within it.

We can create new columns that are a transformation of existing ones. The following code will take the data from column `c` and make it uppercase, putting those results in a new column, called `upper_c`. Then it will show the [[data]] in the whole DataFrame:

```python
df.withColumn('upper_c', upper(df.c)).show()
```

## Applying a function
We can also apply custom [[Python]] functions (see [[functions (python)]]) to PySpark DataFrames in the following way. We have to use a UDF (user-defined function) tool:

```python
import pandas as pd
from pyspark.sql.functions import pandas_udf

@pandas_udf('long')
def pandas_plus_one(series: pd.Series) -> pd.Series:
	# simply plus one by using pandas Series
	return series + 1

df.select(pandas_plus_one(df.a)).show()
```

Note that we have to use [[decorators]] for this.

We could also use `DataFrame.mapInPandas` to use the APIs in a Pandas DataFrame with no restrictions on the result length.

```python
def pandas_filter_func(iterator):
	for pandas_df in iterator:
		yield pandas_df[pandas_df.a == 1]
		
df.mapInPandas(pandas_filter_func, schema=df.schema).show()
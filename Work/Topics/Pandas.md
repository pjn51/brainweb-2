# Pandas 🐼
---
Pandas is an essential [[Python]] [[modules and packages|package]] for datasci. We will be focusing on series and dataframes, which pd-specific [[data types]].

[[Pandas is popular for data science]]. 

## Series
A series is a 1D labelled array. It can hold any data type, but it has to be homogenous. 

We can create a series from a Python dictionary through the following syntax...

```python
import pandas as pd

my_dict = {"Gordon": 20, "Roberto": 10, "Jerod":15} # first create a dictionary
ex_series_1 = pd.Series(my_dict) # then we can transfer the dict into a series
```

This will create a series called ex_series_1 which can be viewed as...

```python
Gordon		20
Roberto		10
Jerod		15
dtype: int64
```

Much easier to read than an array! Wow, we even have labels and can tell what the fuck is happening. 

We can try and manually create an index (label) for the series by calling `pd.Series(my_dict, index = [“Jerod”,”Mary”,”Bob”]`.

This returns the below result because Mary is not in the dictionary of reference. However, Jerod is. 

```python
Jerod	15.0
Mary	NaN
Bob		NaN
```

From the above we can see that python is good about keeping safe the relationship between the data and the label it was assigned to in the dictionary. 

We can create a series from a list.

```python
myseries = pd.series([1,2,3,4])
myseries
```

This returns...

```python
0	1
1	2
2	3
3	4
dtype: int64
```

Since the list doesn't give index names, these names default to ints. 

### Creating a series from a numpy array
```python
my_array = np.arange(2,6) 	# we create an array of one dimension from 2-5. 
Pd_1 = pd.Series(my_array)
```

this creates a series from the array. Since we don't have labels, it will assign 0,1,2,3 as the labels. 

Series even have names! They function as column names, even though there's really only one column in a series. We can use the name argument to set the name. 

## DataFrames
This is the bread-and-butter of Pandas, and therefore [[pd.DataFrame]] needs its own note.

## Time series data in Pandas
Pandas is really good at this. 

There’s usually a single value that we’re tracking over time. 

There are different ways to format this kind of data.

We can use `pd.TimeStamp( )` to keep track of a time stamp.

We can use `pd.to_datetime( )` to convert a string to a timestamp. 

`pd.date_range( )` allows us to specify a start date, frequency, and number of periods for analysis. 

In general, the index is where the time is located in a time series. 
`pd.Period( )` will take a string and interpret it as a time value. 

If we want to resample the data, we can use the `.resample( )` method. For instance, we could change the data from something collected each second to [[data]] minute-by-minute. 

## Further reading
- YouTube channel [Data School](https://www.youtube.com/watch?v=yzIMircGU5I&list=PL5-da3qGB5ICCsgW1MxlZ0Hq8LL5U3u9y&index=1) provides a Q&A series on Pandas. 


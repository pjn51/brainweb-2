# DataFrames in Pandas
`LINKS:` [[Pandas]]
`TAGS:`

---
DataFrames have multiple columns. We can create them from [[dictionaries]] like we can with series. We have to provide the column names as keys, and everything in the rows is in the value section of the dictionary. If we were tracking a plane or something, we could use a dictionary such as 

```python
{‘time’: [0,10,20], ‘lat’:[-312,550,223],’alt’:[1002,12309,23423] }
```

We also have to specify an index which will label each row. 

We can also create DataFrames from [[NumPy]] arrays.

We create an array first, then we use `pd.DataFrame(array,index,columns )` where index and columns are lists of strings that label the data. 

We can create data frames from CSV files, and we can manually input which column and which row we want to be the labels for the data frame. For this, we use `pd.read_csv()`. 

## Inspecting Pandas Data Structures
We need to get information from data structures. This may be the dimensions of the data, the labels / index, or the data itself. There are lots of different kinds of information that we might be interested in when it comes to a specific data set. 

Name | Effect
---|---
`df.head(n)`|displays the top `n` rows of the dataset
`df.tail(n)`|displays the bottom `n` rows of the dataset
`df.describe()`|displays # of rows and columns, basic statistics, obj name
`df.info()`|display the columns, types, rows, and memory used
`df[n].value_counts()`|displays a sum of each value in column *n*


## Pulling data by column
When pulling data from a series or dataframe, we have a few options.
We can pull data from a specified column using `df[column_name]`. This returns a series object. 

We can also pass in `df.column_name`, which has the same function as the above syntax. However, this only works when the column names don't have special characters or spaces in them. 

If we want multiple columns, we can pass in `df[[‘column_name1’,’column_name2’]]` to get all elements in both columns. 

## Pulling by row / index
We can do the same for a specified row, with similar syntax. We pass in `df.loc[row_label,column_label]`. If you want the whole row, just omit the column label. 

We can pull from multiple labels by passing in a list of labels instead of a single one. Pretty simple. 

If we want a range of labels, we can use slicing notation `:` instead of having to pass in every single label. 

We can also slice by integer location, using the index position of the data. If we slice by position like this, we pass in `df.iloc[row_num,column_num]`.

By passing in `df.iloc[2]`, we will pull all elements from the third row. If we wanted a specific element in this row, we could pass in `df.iloc[2,3]`. If we want a couple rows, or a couple columns, pass in a list of index locations for either or both parameters. We can also slice in the standard way. 

## Pulling by boolean test 
Boolean indexing is where we give a boolean vector that determines what elements we want to pull. See [[booleans and logic]].

For instance, if we want to pull all elements in column ‘a’ greater than a given int ‘n’, we can pass in `df.loc[ : , ‘a’] > n`. This will return `True` or `False` for all elements in column a. This boolean series can be used as a selector to pull all elements that returned True for that test. We could do this by passing in `df.loc[df.loc[ : , ‘a’] > n]`.

If we omit `.loc`, and just pass in `df[df > n]`, all the rows that are greater than 4 will be returned. 

We can invert this boolean test, by passing in `df[~(df > n)]`. This will pull the opposite of the above command. 

We can index using `isin` if we pass in a list of values, and get back a boolean vector that can be used in boolean indexing.

For a series, pass in `series_1[series_1.isin([1,2,3])]`. This will return all elements of `series_1` that are contained in the list [1,2,3]. 

## Pulling individual cell
If we want to get an individual value, we can use `df.loc[‘row’,’column’]`. But we could also use a different method. If we pass in `df.at[‘row’,’column’]`, this will also work. The at method can only pull a single value. We might prefer this because it’s a little bit faster.

## Changing values
For a series, we can change the values in the first two elements of a series by passing in `series_name[:2] = n` where n is the new value. This will change all selected elements to the same value.

For data frames, we can do the same syntax to change the values in the first two rows, and this will change all selected elements. If we want to specify a column, we can use the`.loc` method, or the .at method if we are changing the value of a single row or a single column. 

If we want to specify by position, we can use the `.iloc` method. 

## Changing row indices and column names
If we want to rename the indices, we can pass in 
`series_1.rename({‘current index’:’new_index’})`. This also works for dataframes. 

If we want to reset the indices to the standard series of integers starting at zero, we can pass in `series_1.reset_index( )`. This saves the labels in a new column but changes the index to the standard. 

The `.reindex( )` method permanently changes the index without saving the old labels. However, it does not save the data that was associated with the labels which are deleted or changed.

To rename columns, just pass in `df.columns = [ ]`. This will rename all the columns, or you can use a dictionary by passing in `df.rename( {x} )` where `x` is a dictionary relating the old column names to the new ones you want. You can change just a few columns using this method. 

We can make an existing column the new index, using `df.set_index('column')`.

## Adding Rows
We can use the `.concat()` method to combine two series or dataframes. This method takes in the arguments series/df, index, columns. 

We can also use `.loc()` to add a new row to a dataframe, by indexing out of range and setting that equal to a new value or dictionary of values. 

## Removing Rows and Columns
To drop an element from a series, we can drop by label. If we want to drop row a lff a series, we can pass in `series1.drop([‘a’])`. For a data frame, we can do the same if we want to drop a whole row. We can also use `.loc` to specify a column, or a row/col combination. 

## Sorting Rows and Columns
We can use the `.sort_values` method.

```python
my_series.sort_values(by=’column_name’)
```

## Concatenate
We can combine data frames “one above the other” by using `pd.concat([df1,df2])`. 
This will add the rows of df2 to the bottom of df1.

This takes a parameter axis, but defaults to zero. If you want to put the two dataframes side by side, set the axis to 1. 

We could also use the method `df1.append(df2)` to do the same thing.

## Merge
Merging [[data]] frames is a little different from concatenating. Instead of just adding a lot of new rows at the bottom, merge detects which values from data table 2 should be paired up with values from data table 1. This is a way to bring in additional data without losing any relationships along the way. We have to input the parameter we’re merging ‘on.’ Merge brings in all new information that has a corresponding value in the other data frame. It basically brings in the intersection of the new data frame with the other data frame. We can specify a left hand and right hand parameters that we want to use as a reference for merging the data frames. 

**Outer join**: produces a full set of data from both tables, without losing anything at all. Places where the data doesn't exist are null. 

**Inner join**: this is a way to merge producing only the set that’s found in both data frames. It retains only the matches. We do this by changing the ‘how’ parameter in the pd.merge function. 

**Left join**: merges producing a complete set of records from the first data table, and whatever information from the second data table that have corresponding values in the first table. 

## Join
This is a little different than `merge()`. This actually matches on index by default, while you can match on whatever you want when using `pd.merge( )`. By default, it will be a left join. 

## Pivot
We can transform the structure of a table by choosing what we want the index to be, and what we want the columns to be. We pass in 

`df.pivot(index = "a", columns = "b", values = "c")` 

to manually do this.

## Melt
We can take a very wide table (lots of columns) and make it long (lots of rows). We collapse multiple  columns into a single column that contains all the variation. 

## Pivot tables
This allows us to aggregate. We feed it our [[data]], what we want to aggregate, the index name. It will add up all the data. 

## GroupBy
We can use the steps of split, apply, and combine to do quick calculations and get summary stats for exploratory data analysis.

### Step 1: split
We first have to create a groupby object. We aggregate based on a single column value. Pass in `grouped_df = df.groupby(‘parameter’)`. Then we can use the `.sum( )` method to look and see how the data breaks down by this specific parameter. We can also use the`.groups( )`method to look at all the groups present based on this single parameter. We can run the `.describe( )` method to do summary stats based on this single parameter. We can group by multiple columns if we pass in a list of parameters into `.groupby( )`. 

### Step 2: apply
Now, we can run functions on each group and see what patterns emerge in the data. For instance, we can use the `np.sum( )` method. 

We can do lots and lots of different things, like get the [[z-score]] of a specific column based on the way the data is grouped. We can also filter the data within a group. 

## Operations on Pandas Data Structures
Pandas, and the NumPy which it is built on, tries to avoid looping by doing lots of things at the same time. If we want to loop, we can.

We can use the method `df.iterrows( )` to return the index and the value of a data frame at the same time. This is basically looping over the rows of a df. 

```
For row in df.iterrows( ):
	<statement>
```

For a larger data frame, this will take a long time! Try to stick to vectorized operations if you can.

If we want to loop over columns, we can use the `df.iteritems( )`method. 

If we want to apply a function to each column , we can use the `.apply` method. This takes in the function we want to do, and an axis setting that defaults to zero. This is powerful when we apply lambda functions to this. The .applymap method is similar, but is on a column basis. 

## Dealing with Missing values
We can find missing data by using the `.isna()` method which returns a boolean. The `.nonna()` method does the same thing in reverse. 

There are also ways to count the total number of rows or columns that have missing data. 
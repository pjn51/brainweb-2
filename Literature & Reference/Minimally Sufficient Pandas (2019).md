---
author: Ted Petrou
rating:
genre: STEM
format: article
---

# Minimally Sufficient Pandas
`LINKS:` [article](https://medium.com/dunder-data/minimally-sufficient-pandas-a8e67f2a2428) 
`TAGS:`
`AUTHOR:` Ted Petrou

---
## What is minimally sufficient Pandas?
Lots of things in the [[Pandas]] library are overlaps, and can be ignored if you know what the essential tools are. Since multiple ways of doing everything are all over Pandas, this can be very confusing to learn, and for code documentation.

## Selecting a column of data
We can either use brackets, or dots. Always use brackets. There are cases where the dot notation doesn't work, so just use brackets.

If we want to select a column, called var1, from our dataset, use...
```python
import pandas as pd
df = pd.read_csv('data.csv',index_col=0)
df['var1']
```

## Selecting rows
Always use `loc` or `iloc`, never use `ix`. The latter is bad because it tries to select row by either label or integer location. But row and column names can be either strings or ints, so this is confusing. 

Instead, `loc` selects *only* by label, and `iloc` selects *only* by integer location. 

## Finding null values
Always use `isna` and `notna`, don't use `isnull` and `notnull`. These do exactly the same thing. 

## Arithmetic
There are multiple ways to add, subtract, multiply, and divide. We can use the built in python way, and the pandas way. 

For example, `+` does the same thing as `add`. `-` does the same thing as `sub` or `subtract`.

However, there are a few cases where we need to `multiply` instead of using `*`.

### Case study in arithmetic methods / operators
Let's say we have a dataframe of a bunch of college stats, `college_idx`. It contains the relative frequency of each racial group in a bunch of universities. If we want to get all the racial data in its own dataframe, we select the first column,`ugds_white` and the last, `ugds_unkn`, we can put them in their own dataframe in this way...

```python
college_race = college_idx.loc[:,'ugds_white':'ugds_unkn']
```

Inside the [], we are specifying that we want all rows (:) and we specify the starting column and ending column for the new dataframe.

So now that we have the relative frequency of different racial groups per school, we need to find the raw count of the student body. We can get this by multiplying the relative frequency of a school's (row) ethnic group by the total student body which is found in `college_idx`. 

Intuitively, it seems like we should be able to run `collge_idx['udgs'] * college_race`. But this doesn't work, since it turns the column from `college_idx` sideways and just fucks everything up. 

![everything messed up|500](https://miro.medium.com/max/1400/1*X3bdE6iFrFKTLLqrkipLAg.png)

Instead, we have to change the direction of the alignment manually using a method. We can't do this using `*` since there are no parameters to change. But with `mul`, we can change the parameters.

```python
race_totals = college_race.mul(ugds,axis='index').round(0)
```
This code will get us the correct output. 
![correct|500](https://miro.medium.com/max/1400/1*82_NlxL9Dt_c1BiiJQgB6A.png)

Overall, just use the operators, but remember that sometimes we have to use methods if we want to be more specific. 

## Duplicate methods
Some pandas methods have built-in duplicates. These include...

```python
sum()
min()
max()
abs()
```

We should use the pandas ones because they're faster. 

## Standardizing groupby aggregation
There are a lot of ways to write the syntax to do this. Choose one and stick to it so that your code is readable. 

```python
df.groupby('grouping column').agg({'aaggregating column':'aggregating function'})
```
# Sets
`TAGS:`

---
# Introduction
A set is a [[data types|data type]].

There are two kinds of sets in Python. There are sets and frozensets. Frozensets are immutable, but default sets are mutable. They’re unordered, so you can't index them. 
A set extracts all the unique values of a list.

Sets are defined as `my_set = { }`. However, this is the same way a `dict` is created. Python doesn't know it's a set until you populate it. 

*I missed a good chunk of this lecture, so I need to review the Jupyter Notebook when I get a chance*

We can use the `set()` function to remove duplicates from lists. 

Instead of index assignment, we have to use the `update( )` method to change elements in a set. 

Set methods
- `.update( )`
- `.remove( )`
- `.add( )`
- `.discard( )` 
	
`discard()`  is different from `remove()` because it will not return an error if the item to be discarded isn't in the set.

```python
mylist = [1,1,2,3,3,4,5,5]
myset = set(mylist)
myset
```

This returns `{1,2,3,4,5}`
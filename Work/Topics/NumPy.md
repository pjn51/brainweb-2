# NumPy
`LINKS`: [[Python]]


---
NumPy is the numerical [[modules and packages|package]] standard in python. Everything math has a place in numPy. We mainly use NumPy in [[data science]] for its arrays and math functions. 

# Arrays
Arrays are a big deal in NumPy. These work faster than lists or other [[data types]]. In general, NumPy is really fast and can process a lot of information very quickly. 
Axis: an array’s axis refers to the number of dimensions in the array. 

Rank: this refers to the number of axes in the array. 
EX: an array with two dimensions has two axes and has rank 2. 

Length: the number of elements in each axis. 

While Python has a built-in array, it's an afterthought. We will only use arrays from NumPy. 

We initialize an array by calling `np.zeros(x)`, where x is the shape of the array (basically the length). 

## Array printing rules
The last axis always prints from left to right.
All other axes print from top to bottom.  

```python
Zero = np.zeros((4))
Zero
```

Will return...

`array([0., 0., 0., 0.])`

This is an array filled with zeros of four rows. This array has a single dimension. 

```python
one = np.ones((2,3), dtype = np.int)
one
```

Returns...

```python
array([1,1,1],
	[1,1,1])
```

This creates an array with two rows, and three columns. 
We can initialize an array with a given number...

```python
full = np.full((4,3,2), 10)
full 
```

Returns...

```python
array([[[10,10],
	[10,10],
	[10,10]],

	[[10,10],
	[10,10],
	[10,10]],

[[10,10],
	[10,10],
	[10,10]]])
```

This creates a 3D array with 4 rows, 3 columns, and 2 elements deep. 
Remember, the last axis (in this case 2) will always print horizontally. That means that we see the return above. 

## NumPy array methods
`.ndim` returns the dimensionality of an array
`.size` returns the total number of values
`.dtype` returns the array type
`.isnan` returns a boolean indicating if the element is null (‘nan’)
`.diagonal` returns diagonal elements from a 2D array, starting with row 0, index 0
`.arange` returns a 1D array with a list of numbers corresponding to their indices. 
`.flat` changes the shape of the array to a 1D. 

## Indexing and slicing
This can be tricky in arrays.
`my_array[0:3]` will return the first three elements in a 1D array, like normal. 

### For a 2D array
`my_array[1:2]` will return the second row in its entirety. 

If you want specific elements of a specific row, you need to use `my_array[1:2,1:3]`. This will return items 2-3 on row 2. 

Standard slicing notation in terms of step apply here. We can index backwards or skip by intervals through the data. 

If we want to return all of a specific axis, we can use `my_array[... , 0]`. In a 2D array, this would give us the first column in all rows. 

We can use the `.ix` method in order to grab specific elements, using the form `my_array_2[([0,0,2,2], [0,2,0,2])]`. This would fetch the corners of a 2x2 array. 

We can return a grid of booleans with...

`my_array > 5`

This will return `True` for every element of `my_array` that is greater than 5. 

## Changing array shape
There are a number of methods that we can call in order to change the shape of an existing array. I have no idea how this doesn't destroy the relationships in the data...
`np.r_` will allow you to combine arrays next to one another in a single row, while `np.c_` will allow you to combine one above the other

## Broadcasting
When trying to combine arrays that are the same shape, there's really no issue. You can call `array_1 + array_2` and get a result. But when the shapes are different, numpy tries some stuff. 

If you try to add a 4x3 and a 3x3, NumPy will align the smaller array to the same axis that it shares with the larger one and stretch the data so that the arrays are the same size and shape. 

If neither dimensions match, like a 3x3 with a 4x4, the smaller array will be stretched in both directions.
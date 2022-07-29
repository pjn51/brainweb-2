# Lists


---
Lists are among the most common [[data types]], along with strings and integers. We need to be familiar with them and understand how to manipulate them. 

## Sequence Types
A list is one of multiple sequence types. A sequence type is a data object that can be indexed, or one that has multiple elements inside of it that can be manipulated. 

List, strings, tuples, and ranges are sequence types. 

They can be mutable or immutable. Lists are mutable. 

Lists are supposed to be homogenous, but can technically contain all sorts of [[data]] types inside of them. But best practice is to stick to one data type for a single list. 

Lists are usually created by  `new_list = [ ]` but can also be created using the `list()` function. I’m not sure why you would need to use this function instead of just doing the standard method. 

## Indexing and slicing
There are lots of ways to index and slice lists in order to get at their contents. Of course, we can use `my_list[0]` in order to get the first element of `my_list`. Python starts counting at zero. 

Multi-element indexing is called slicing. In order to do this, we use the format `my_list[start:stop:step]`. This lets us specify where to start the slice, where to end the slice, and how many spaces to go in between each “pull” from the list. For instance, if you wanted to get the even numbers from the list [0,1,2,3,4,5], you would use the slice `my_list[0:6:2]`. 

If you don't specify a step in your slice, it will default to a value of one. This means that every index between the start and stop you provided will be included in the slice. If we omit the ending index, the slice will include the rest of the list. Similarly, if we don't include a starting index, it will default to zero. 

An indexing procedure will return the data type of whatever lies at the specified index. However, a slice’s data type will always be a list, regardless of what is inside of it. 

## Negative indexing and backwards slicing
An index of [-1] will return the object at the very end of the list. It’s as if the program is counting through the list backwards, wrapping the list onto itself from position zero. 

When the step size is a negative number, the slice will step backwards through the list. This means that your ending index needs to be lower than the starting index or else the code will break. 

## Nested Indexing
If you had a list such as `nest = [0,1,[a,b,c],3]`, and you wanted to get to the letter b, you would use the index `nest[2][1]`.

## Indexing out of range
When indexing, if you provide an index out of range, you’ll get an error. However, if you're slicing, the computer will interpret an out of range starting or stopping point as simply the end of the list, just like when you omit the stopping index. 

## Membership test operations
If we want to find whether or not an object is in a list, we can use the `in` operator. 
“ “ will always return True if you ask if “ “ is in a list, but the command `[ ] in my_list` will return `False`. 

The `in` command only looks at the elements on the first level of a list. If some element is deep inside a nested list, in won't recognize that it's inside there. 

## Actions that can be performed on lists
We can find the length of a list using `len()`.

We can find the minimum or maximum value in a list using `min()` and `max()` functions.

We can find the index of the first occurrence of a given value using` .index( ) `or we can count how many times a given value occurs using `.count( )`
We can sort lists using `sorted( )` or using `list.sort( )`

## Changing elements of lists with indexing
We can append lists (add elements to the end of them), or we could use a slice to do this manually. 

The extend method adds a new portion to the end. 

The difference between these two actions is that append adds the new object as a list, while extend adds it to the original list. 

## Removing items from a list
We can write `del mylist[2]` to remove whatever is at index 2 of mylist. We can also use standards slicing notation with the del function. 

Another possibility is to just say `mylist[2] = [ ]` in order to overwrite index 2 of `mylist`. 

If you want to remove a specific item but don't know the index, use the remove method. `mylist.remove(‘a’)` will remove the first instance of ‘a’ in mylist. 

The `pop()` method will also work to remove something at a specified index. 
`mylist.clear( )` will empty the whole list. 

## Copying Lists
There are a few ways to copy lists. In general, we can just assign a new variable to equal a list. This new variable points to the original object, so when we update the original list, the new list also changes.

If you don't want this to happen, you can do a shallow copy
By using the method `list.copy( )`, you can say `new_list = original_list.copy()` to create a separate entity in the computer memory. 

This can also be done using slicing notation. 

However, if the original list is a nested list, the two lists still share one position in memory on the second layer down. If you update the second layer in the original list, it will update both lists

## Deep copy
If you import a module called `copy`, you can use the method `deepcopy` to create an independent nested list that can be changed without worrying about the original also changing, or vice versa. 

Side Note: It seems like our instructor always calls algorithms ‘algos,’ I guess this is the cool way to talk about them. Better talk like that in an interview...

See this note for more on [[copying]].

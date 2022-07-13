# Range

---
# Introduction 
`range()` is a [[functions (python)|function]] in [[Python]].

A range uses notation similar to a slice. They are defined by a start, stop, and step that you define. They’re very memory efficient, because they only save these three numbers, instead of a list of all the numbers in between. We have to use the function `list()` in order to see the whole set of numbers in that range. 

If we say` list(range(10))`, this will print a range of integers from zero to nine. 

If we say` list(range(1,10))`, this returns a range of integers from one to nine. 

If we say` list(range(1,10,2))`, this returns a list of numbers from one to 9, but only every other number because we've set a step of 2. 

All the standard slicing notation applies to ranges, so that’s how we can make ranges go ‘backwards’ if we want

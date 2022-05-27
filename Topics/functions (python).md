---
aliases: [function, functions]
---
# Functions

---
# Introduction
We’re heading into the more [[data science]] specific stuff for [[Python]], but first we have to wrap up the last of the basic programming knowledge you need to know before we dive into the packages and modules for [[data science]]. 

After tonight, we can start playing around and writing our own algorithms.
Functions take an input, and provide an output. That’s their basic structure. This is written as...

```python
def func_name(input) :
	"""
	This is the docstring
	"""
	
	<statement>
	
	Return output
```

We don't need to know how every function in the world really works, but we need to know enough to understand how to use it and which function we should use for a given task. 

The docstring should describe what the input parameters are, and what the code should be used to do. 

# Arguments
An argument, or ‘arg,’ can be a positional argument or a keyword argument. A keyword argument relies on the direct assignment of an input to a variable. 

A positional argument relies on the placement in order of the input parameters. Each parameter doesn't get assigned to a variable. 

Using `kwargs`, you don't have to have the inputs in the same order each time you run the function. 

## Rules for argument usage
1: if a function uses both positional args and kwargs, you need to have the positional ones first. 

2: All `kwargs` must have a place in the code where the variable is used. 

3: No argument can receive two inputs. 

# Arbitrary assignments
We can use `*` to indicate that we are passing in a list of values to the parameters of a function. For instance, if we had a function that summed a given set of parameters, like `sum(a,b,c)`, we could create a variable called `mylist` that had three integers, and then execute the command `sum(mylist*)`. This would assign each element of mylist to a, then b, then c. 

Remember, the `return` statement will end the execution of the function. If anything is after return, it won't be executed! If you need to output multiple things, just assign whatever you need to output to a variable, and then return that variable at the very end. 

# Scope
Scope can be either global or local. Global scope refers to all the variables outside of the function in question. We can access these at any time. Variables that have a local scope can only be accessed inside the function in which they live. 

In order to make a local variable into a global one, we have to declare that the variable is global right before we define it. We use the command `global my_variable` in order to make `my_variable` into a global variable. 

# Lambda Expressions 
These let us use small, anonymous functions without having to define them concretely. This just saves time and space. 

These really shine when we use them with other functions, like `map( )`, `filter( )`, or `reduce( )`. When we use them in conjunction with more complex procedures, this will make more sense. 

Classic function:

```python
def exponentiate(num):
	return num**2
```

Or...

`lambda num: num**2`

The above function would take an input num and immediately output `num**2`, saving a little time when compared to a classic function. 

These are inherently limited to a single line of code. 

# Map, Filter, and Reduce 
## Map
We can use the `map( )` function to apply a given function to every element of an iterable. 

`print(list(map(fahrenheit, celsius_input)))`

This line of code would apply the `fahrenheit( )` function to every element of the `celsius_input ` list, combine these outputs into a list, and then print them. 

We can get even more efficient. Instead of creating a fahrenheit function, we could use a lambda expression...

```python
print(list(map(lambda celsius_input: (9/5)*celsius_input + 32, celsius_input)))`
```

How quick, how swift!

If you want to write a one liner to take a sentence, break it into words, and then tell you in a list how many letters are in each word...

```python
list(map(lambda x: len(x), sentence.split()))
```

Pretty slick. 

## Filter
This function allows us to trim an iterable by removing all elements that cause a False output from a given function. 

For example, if we want to remove all elements of a list under 3, we can write a function that checks to see if the num is greater or equal to three, and returns a boolean. We can then use the filter function with a lambda expression similar to how we did so above using map.

## Reduce
This function comes from the module `functools`. 
It’s similar to `map`, but it can be used to create a rolling sum of a list. Not sure what this one really does...
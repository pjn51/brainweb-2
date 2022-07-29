---
author: Geir Arne Hjelle
rating: WIP 
genre: STEM
format: article
---
# Primer on Python Decorators
`LINKS:` [source](https://realpython.com/primer-on-python-decorators/)
#article #wip 
`AUTHOR:` Geir Arne Hjelle

---
In this tutorial, the article says, we will learn what [[decorators]] are and how to use them in [[Python]]. They provide a simple syntax for *higher-order functions.* Decorators are defined as functions that extend the behavior of other functions without explicitly modifying them. 

# Functions
The author runs through a basic example of [[functions (python)]]. They return a value based on some given arguments. 

# First-class objects
In Python, the author remarks, functions are *first-class objects.* This means that they can be passed around and used as arguments just like any object such as [[strings]] or [[lists]]. Consider the following:

```python
def say_hello(name):
	return f'Hello {name}'

def greet_bob(greeter_func):
	return greeter_func('Bob')

>>> greet_bob(say_hello)

'Hello Bob'
```

# Inner functions
The article explains that we can also define functions inside of other functions. These child functions will only return something if they are called within the parent function. They only exist within the parent function, so we cannot call them elsewhere. 

# Returning functions from functions
Just like we can call child functions inside of a parent function, the author says, we can also return functions within the parent function. 

# Simple decorators
The article begins with a simple decorator for an example. 

```python
def my_decorator(func):
	def wrapper():
		print('Something is happening before the function is called.')
		func()
		print('Post function statement.')
	return wrapper

def say_whee():
	print('Whee!')
	
say_whee = my_decorator(say_whee)
```

Now, the author explains, we can pass this function and see what happens.

```python
>>> say_whee()
'Something is happening before the function is called.'
'Whee!'
'Post function statement.'
```

The author clarifies that decorators *wrap* a function, modifying its behavior. 

# Syntactic sugar!
The article demonstrates a good shortcut. Instead of having to pass `say_whee = my_decorator(say_whee)`, we can simply pass `@my_decorator` right above `say_whee()`. 

# Reusing decorators
The article reminds us that decorators are just normal functions, and we can use all the other tools that we might use for a function. 

```python
def do_twice(func):
	wrapper_do_twice():
		func()
		func()
	return wrapper_do_twice

@do_twice
def say_whee():
	print('Whee!')
	
>>> say_whee()
'Whee!'
'Whee!'
```


---
author: Corey Schafer
rating: WIP 
genre: STEM
format: video
---
# Python Tutorial - Decorators (2016)
`SOURCE:` [source](https://www.youtube.com/watch?v=FsAPt_9Bf3U)
`TAGS:` #wip #video
`AUTHOR:`Corey Schafer

---
# Simple example
Here is a decorator that just runs the original function without doing anything. 

```python
def decorator(original_function):
	
	def wrapper_func():
		original_function()
		
	return wrapper_func()

def display():
	print('display func ran.')
```

```python
>>> decorated_display = decorator(display)
	decorated_display()

'display func ran.'
```

# A more useful example
We can easily add functionality to existing functions by adding more statements inside the wrapper function. 

```python
def decorator(original_function):
	def wrapper_func():
		print('wrapper output')
		return original_function()
	return wrapper_func()

def display():
	print('display func ran.')
	
decorated_display = decorator(display)
```

```python
>>> decorated_display()
'wrapper output'
'display func ran.'
```

# Syntactic shortcut
The following two statements are identical:

```python
# new syntax
@decorator
def display():
	print('display func ran.')
	
# is the same as...

decorated_display = decorator(display)
```

Now we need to be able to pass any number of arguments to a wrapper function, so that we can reuse decorators. We can use this with keyword arguments, or kargs. We can update the `decorator()`...

```python
def decorator(original function):
	def wrapper(*args, **kwargs):
		print('wrapper output')
		return original_function()
	return wrapper_func()
```

Now `decorator()` can be applied to any original function. 

# Using classes as decorators
```python
class decorator_class(object):
	
	def __init__(self, original_function):
		self.original_funcion = original_function
		
	def __call__(self, *args, **kwargs):
		print('call method output')
		return self.original_function(*args, **kwargs)
		
```

Now we can run the following functions with this decorator...

```python
@decorator_class
def display():
	print('display function ran')
	
@decorator_class
def greeter(name):
	print(f'hello {name}!')
```

```python
>>> display()
'call method output'
'display function ran'

>>> greeter('Patrick')
'call method output'
'hello Patrick'
```

# Practical examples
If we want to log how many times a function was run, we can use a decorator. This following function can act as a decorator that logs the function, including what arguments and keyword arguments the fucntion was run using, and then return the output of the original function. 

```python
def logger(original_func):
	import logging
	logging.basicConfig(filename='{}.log'.format(orig_func.__name__), level = logging.INFO)
	
	def wrapper(*args, **kwargs):
		logging.info (
			'ran with args: {}, and kwargs: {}'.format(args, kwargs))
		return original_func(*args, **kwargs)
	
	return wrapper
```

```python
@logger
def greeter(name):
	print(f'Hello {name}')
	
>>> greeter('Patrick')
'greeter ran with arguments ('Patrick')'
```

We can also use a decorator to time how long a function takes to run. 

```python
def timer(original_func):
	import time
	
	def wrapper(*args, **kwargs):
		t1 = time.time()
		result = original_func(*args, **kwargs)
		t2 = time.time() - t1
		print(f'{orig_func.__name__} ran in {t2} seconds.')
		return result
	
	return wrapper

@timer
def greeter(name):
	print(f'Hello {name}')
	
>>> greeter('Patrick')
'greeter ran in 0.00 seconds.'
'Hello Patrick'
```

# Chaining decorators
We can actually apply multiple decorators to one function!

```python
@logger
@timer
def greeter(name):
	print(f'Hello {name}')
```

However, we need to be very careful with the order that these wrappers work in. 
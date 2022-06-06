---
author: Metis
genre: STEM
format: article
---
# Simple Introduction to Unit Tests (2021)
`SOURCE:` [source](https://github.com/thisismetis/NBM_Engineering_Student/blob/main/curriculum/unit-testing/simple_introduction_to_unit_tests.ipynb)
`TAGS:` #wip 

---
This is a [[Jupyter Notebook]] provided by [[Metis]] about unit testing.

# Unit testing: how we make sure our code doesn't break 
The article begins by saying that software engineers love unit testing, and that it's the idea that we want to make sure the functions we write are behaving correctly. 

We start with a simple example of a function that adds two to an input:

```python
def add_two(input_int):
	return input_int + 2
```

If we want to make sure that nobody is providing a typo or something, we can use `assert` to automatically test the function as it runs.

```python
def test_add_two():
	assert add_two(4) == 6, "test 1 failed."
	assert add_two(4.7) == 6, 'test 2 failed.'
	return 'passed.'
```

The above function runs `add_two()` and tests what the output is. If we run this, we will see that `add_two()` fails test 2, since it doesn't enforce an integer data type. We can rewrite our original function so that it won't have this issue:

```python
def add_two(input_int):
	return int(input_int) + 2
```

This is unit testing in a nutshell. We write lots of tests and run them to make sure our functions are doing what we want them to do. 

We should consider a few questions when writing unit tests...

# What are the edge cases?
An edge case is a non-obvious way that a function would break down. We should consider all the ways that code could be mis-used and prepare for them by writing edge cases into our unit tests. 

# How should your code break?
We should be conscious of what sort of errors will appear when the code breaks, and make sure that the correct ones appear. To help with this, we can use the `unittest` library. 

This library assumes that we're gonna create a class of tests to work on something. Let's work on an example by creating a class that inherits from a built in class from `unittest` called `TestCase`.

```python
import unittest

class TestStringMethods(unittest.TestCase):
	
	def test_upper_lower(self):
		'''
		This test makes sure that the '.upper' method is working
		correctly. 
		'''
		self.assertEqual('foo'.upper(), 'FOO')
		
	def test_is_upper(self):
		'''
		This test makes sure the '.isupper' method is working.
		'''
		self.assertTrue('FOO'.isupper())
		self.assertFalse('Foo'.isupper())
		
	def test_split(self):
		'''
		This test makes sure the '.split' method is working.
		'''
		s = 'hello world'
		self.assertEqual(s.split(), ['hello', 'world'])
		
		# now we check to make sure s.split fails when using a non-string
		with self.assertRaises(TypeError):
			s.split(2)	
```
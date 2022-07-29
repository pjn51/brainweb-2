---
aliases: [unit tests, unit test]
---
# Unit Testing


---
# Introduction
Unit testing is a practice in [[data engineering]] to make sure that we're catching errors in our code. We can use the `unittest` library to help out. 

# Simple example
If we have a function that adds two to an integer input...

```python
def add_two(num):
	return num + 2
```

... we may want to make sure that it does what we think it does. 

```python
def tester():
	assert add_two(2) == 4, 'Test 1 failed.'
	assert add_two(5.1) == 7, 'Test 2 failed.'
```

If we run `tester()`, we will see that test 2 has failed since the original function isn't making sure `num` is an integer. 

# A more realistic example
Usually, we would have our unit tester be a c
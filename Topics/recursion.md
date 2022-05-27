# Recursion
`TAGS:`

---
# Introduction
Recursion is the process of writing [[functions (python)]] that call themselves. This can be done relatively easily in [[Python]]. 

# A simple example
We can create a function that just prints a statement. 

```python
def greet():
	print('hello')
```

If we want to call this over and over, we could do either of these approaches...

```python
# using a for loop

for i in range(10):
	greet()
	
# using recursion

def greet():
	print('hello')
	greet()
```

This second method above will call greet an infinite amount of times. Python will limit this to 1,000 recursions by default. If we want to see the recursion limit, we can pass `sys.getrecursionlimit()`. To increase this limit, we can pass `sys.setrecursionlimit(n)` where `n` is the new recursion limit. 

# A more compex example
We can create a function to calculate factorial using recursion. 

```python
def factorial(n):
	if n == 0:
		return 1
	
	return n * factorial(n-1)
```


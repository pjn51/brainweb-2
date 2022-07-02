# Errors
`TAGS:`

---
## Introduction
We must learn from our mistakes or we are doomed to repeat them. [[Python]] issues various kinds of errors when things go bad. 

## Error variants
Syntax errors happen when we spell something wrong or misplace a comma or something like that. 

An exception is a specific kind of error where we have broken one of Python’s rules. For instance, we may have tried to iterate through an object that isn't iterable, or we tried to index out of range. 

[[Jupyter Notebook]] is friendly and will tell you exactly what kind of error you have made, and where you made it. It will not judge you or talk about you behind your back to the other IDEs. 

Name errors occur when you try and call something that doesn't exist. 
There are lots more types of errors, most of them are pretty intuitive. 

## Exception handling
We can choose what happens when a specific error happens. This is very useful when making projects. 

```python
try:
	#insert your code you want to run
except SyntaxError : 
	print(“You made a syntax error.”)
```

The above example would return the string given if you made a syntax error. You can have except statements for all kinds of errors, or you can choose to pass a single message for any kind of error by not specifying anything after `except`. 

Using this tool will also allow the program to continue past the error if possible. 

## Time-out errors
If you want to make sure your computer doesn't explode, use a `TimeoutError`. Just make a counter object like `time` that increases every iteration of your loop or something, and then use the syntax below. This acts as a `break` with a message on it. 

```python
If time > 10000:
	raise TimeoutError(“Your computer timed out.”)
```
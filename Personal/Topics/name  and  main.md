# __name__ and __main__
`TAGS:`

---
When we create a [[Python]] script, we are sometimes doing so in order to run that script. If that is the case, we want all the code we wrote to actually execute when the script is run.

However, this is not always the reason we use a .py file. What if we just want to import the functions from another .py file, but not actually run them right away? In this case, we wouldn't want the functions to execute when we call the file.

We can solve this problem using a couple built-in variables, and a simple `if` [[loops|loop]]. 

`__name__` is a built-in variable in our scripts. When you run a file, `__name__` is set equal to another built-in variable, `__main__`. 
 
If we want to check if the .py file is being run directly, or is being imported into another .py file, we can pass...

```python
def myfunc():
	<statement>

if __name__ == __main__:
	myfunc()
```

This last part means that when the file is being run directly, `myfunc()` will run when the file is called. However, if `__name__ != __main__`, then the last part of the code will not execute, and the only thing that will happen is that the function or functions in the code will be created. 
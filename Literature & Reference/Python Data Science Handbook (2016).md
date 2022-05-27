---
author: Jake VanderPlas
genre: STEM
---
# Python Data Science Handbook
`LINKS:` [source](https://jakevdp.github.io/PythonDataScienceHandbook/index.html)
`TAGS:` #book #wip
`AUTHOR:` Jake VanderPlas

---
# 1. Preface
The book says that it's hard to nail down what [[data science]] exactly is. Some have dismissed the label as meaningless, but the author argues that the term captures the cross-disciplanary nature of the field. 

<center>
	<img src='https://jakevdp.github.io/PythonDataScienceHandbook/figures/Data_Science_VD.png'>
</center>

The author says data science consists of the intersection of [[statistics]], computer science, and specialized domain expertise that allows the data scientist to formulate the right questions and contextualize the answers. 

The author says that while Python wasn't designed for data science, it has emerged as a first-class tool due to some outstanding third-party packages. 

While the author admits the PyData world is much larger than five packages, the book is divided into five sections:
1. IPython and Jupyter
2. NumPy
3. Pandas
4. Matplotlib
5. Scikit-Learn

The book explains that there are two methods of using IPython: the IPython shell and the IPython notebook. This book's examples will be relevant to both, and will use whichever is most convinient.

The book says we can launch IPython by passing `ipython` in the [[command line]]. 

The author says we can launch the python kernel needed for the browser-based [[Jupyter Notebook]] by passing `jupyter notebook` in the command line. 

The author emphasizes that finding answers to questions is a critical data science skill. He says that IPython shortens the gap between documentation and the user. 

The book explains the nature and purpose of a *doc string,* which we can access by passing `help(<function>)`. This will return a little text telling us about how `<function>` works. We should always [[Write legible code]]. 

The author says we can also access documentation by passing `<function>?` in order to get the documentation of how `<function>` works.  He says this also works for methods or objects such as [[lists]]. 

The author turns to an example of creating our own doc string...

```python
def square(a):
	'''
	Return the square of a.
	'''
	return a**2
```

By passing `squre?`, the author explains that we can get this doc string. 

The book reveals that we can access the source code of an object by passing `??` after the object's name. The author notes that this only works when the source code is compiled in Python, not in [[C]] or another [[programming language]]. 

The author says we can see a list of methods that are associated with an object by passing `<function>.<TAB>`. The author says we can perform the tab completion trick when importing things as well. 

The author explains that if we know part of the method's name, we can use the `*` character to match it in the list. By passing `*Warning?`, we can see all the objects in the namespace that end with `Warning`. 

# 2. IPython
The author says that the IPython shell has a number of shortcuts that can speed our work up. 

| keystroke | Action                       |
| --------- | ---------------------------- |
| Ctrl-a    | move cursor to start of line |
| Ctrl-e    | Move to end of line          |
| Ctrl-b    | Move cursor back 1           |
| Ctrl-f    | Move cursor forward          | 

| keystroke | action                    |
| --------- | ------------------------- |
| ctrl-d    | delete next char          |
| ctrl-k    | cut following line        |
| ctrl-u    | cut preceding line        |
| ctrl-y    | paste previously cut text |
| ctrl-t    | transpose prev 2 chars    | 

| keystroke | action                  |
| --------- | ----------------------- |
| ctrl-p    | access previous command |
| ctrl-n    | access next command     |
| ctrl-r    | reverse search          | 

The author explains that these actions navigate the history of commands within the IPython shell. He says that all previous commands are stored in a SQLite [[database]] in the IPython directory. 

Turning to the last command, the reverse search, the author explains its use. He says that we can enter a search term and find that within our previous code. When we press `ctrl-r`, we will see this popup:

```
reverse-i-search)`':
```

using this, we can enter a search term. 

| keystroke | action                |
| --------- | --------------------- |
| ctrl-l    | clear terminal screen |
| ctrl-c    | interrupt python      |
| ctrl-d    | exit IPython          | 

The book explains that IPython has some unique commands that are prefixed with `%`. There are two kinds, either *line magics* prefixed by `%` or *cell magics,* prefixed by `%%`. The latter operate on the whole cell while the former operate on a single line. 

The author says that pasting code blocks can lead to unexpected errors due to formatting problems. Consider the following function:

```python
>>> def donothing(x):
...		return x
```

The author says that if we paste this from a website, we will get a syntax error because of too many indents. Instead, we should put a command at the top of the cell in which we want to paste the new code:

```python
%paste
>>> def donothing(x):
...		return x
```

According to the author, this will clean and run the code for us. Similarly, we can paste multiple chunks at the same time using `%cpaste`.

The book explains that we can easily run other `.py` scripts within an IPython kernel using `%run`.

If we have a script containing a function, the book says, we can import that function and run it within an IPython session as follows. This will also store all functions within that script for later use in this session.

```python
%run myscript.py
```

The author notes that another useful magic function is `%timeit`, which tells us how long it took to execute a single line of Python. If we want to see how long `myfunc()` takes to run, we can pass...

```python
%timeit myfunc()
```

If we want to time a whole cell, the book continues, we can pass `%%timeit` at the top of the cell. 

The book reveals that when we tell Python to create inputs and outputs by writing and executing code, these get saved to `In` and `Out` variables which consist of lists of the inputs and outputs. 

The author says we can print the previous output by passing `print(_)`. We can pass `print(__)` to get the second to last output, and so on. 

The author says we can suppress output by putting a semicolon at the end of the line. This is useful for plotting where we don't need to see the output of each line to see the plot. 

The book notes that we can get a batch of previous inputs all at once by passing `%history`.

The author states that it can be frustrating to switch between windows to see tools and system command line tools. IPython bridges this gap and gives us syntax for executing shell commands from within the IPython terminal. This uses an exclamation point. 

The book says that this will just be a quick introduction. Operating systems have existed long before graphical user interfaces, and most active data scientists use shells sometimes since they tend to be faster to use than other tools. 

```
osx:~ $ echo "hello world"					# echo is like Python's print
hello world

osx:~ $ pwd									# pwd = print working directory
/home/patricknorman							# this is the path we're working in

osx:~ $ ls									# ls = list working dir
notebooks projects

osx:~ $ cd projects/ 						# cd = change directory

osx:projects $ mkdir myproject				# mkdir = make directory

osx: myproject $ mv ../myproject.txt ./ 	# mv = move file. we move myproject.txt from
											# one dir up to the current dir

```

The author notes that this is just a new way to perform familiar operations. 

The author explains that any command prefixed by `!` will function as a shell command within python. For example, we can pass `!ls` to list the files in the current working directory. 

The book explains that we can make shell commands interact with the IPyton namespace. We can save the output of a shell command to a list using the following code:

```python
In [1]: contents = !ls
	
In [2]: print(contents)
['myproject.txt']
```

The author reminds us that these will not automatically save as a list object, but will be a special shell return type that python defines. 

The author says that if we want to change the working directory from within IPython shell, we must pass `%cd` 

The author says that since coding requires a good deal of trial and error, we should become familiar with errors and what they mean. 

The author tells us that when a Python script fails, it will raise an exception. We can find info about the error in the *traceback* that will be provided by our Python interpreter. We can change the amount of information displayed in the traceback using the `%mode` magic function. We can set the mode as either `Plain`, `Context`, or `Verbose` to change the level of detail that we get in the error message. 

Within IPython, the book explains, there is a built-in debugger called `ipdb`. We can easily access this by using the `%debug` magic command. This tool will allow us to step through the function and see what's happening line by line. 

| command      | description                             |
| ------------ | --------------------------------------- |
| `list`       | show current location in file           |
| `h(elp)`     | show list of commands                   |
| `q(uit)`     | quit the debugger                       |
| `c(ontinue)` | quit the debugger, continue the program |
| `n(ext)`     | go to the next step of the program      |
| `<enter>`    | repeat the previous command             |
| `p(rint)`    | print variables                         |
| `s(tep)`     | step into a subroutine                  |
| `r(eturn)`   | return out of a subroutine              | 

The author describes how when we develop code and data processing pipelines, we may have tradeoffs to balance. Once things are working, we should seek to optimize them and make things more efficient. We can do this through checking the execution time of various commands. 

The book lists some commands that will be useful for this.
- `%time`: time the execution of a single statement
- `%timeit`: time repeated execution of a single statement for more accuracy
- `%prun`: run code with the profiler
- `%lprun`: run code with the line-by-line profiler
- `%memit`: measure the memory unit of a single statement
- `%mprun`: run code with the line-by-line memory profiler

The book notes that the last four commands don't come installed already, and are part of the `line_profiler` and `memory_profiler` extensions. 

We already saw this in a previous section on magic commands, so I'm going to skip it.

The book defines a program as a collection of statements, and says that we may want to time these statements in context. If we define a function `sum_of_lists(n)`, we can profile this function by passing `%prun sum_of_lists(10)` where we want to have `n=10`. 

If we want to have a line-by-line version of the previous tool, the book explains, we can install `line_profiler` and use the `%lprun` tool. 

# 3. NumPy
The author begins by outlining that the first step in any data processing is to transform the input into something that is machine readable and can be interpreted as an array of numbers. 

For this reason, the author continues, we need to store and manipulate arrays of numbers efficiently. For this, we can use the [[NumPy]] package.

The author asserts that we must understand how data is stored and manipulated in order to effectively perform data science. This section outlines how arrays of [[data]] are handled in Python and how NumPy improves on this handling. 

Turning to an example in the [[C]] language, the author says that each variable has to be explicitly declared. We have to specify a particular operation as follows:

```C
int result = 0;
for(int i=0; i<100; i++){
	result += i;
}
```

The author compares this to the Python implementation:

```python
result = 0
for i in range(100):
	result += i
```

The book underlines the key difference between these two langauges. In C, the data type of each variable is declared while in Python the data types are inferred. This means that we can change the data types of variables in Python whenever we want by passing a new value to the variable. 

The book says that the standard Python implementation is actually written in C. This means that when we create a variable in Python, we are really creating a disguised C structure that contains its value along with other information. An integer actually looks like this:

```C
struct _longobject {
	long ob_refcnt;
	PyTypeObject *ob_type;
	size_t ob_size;
	long ob_digit[1];
}
```

The book lists what each of these things means. 
- `ob_refcnt` is a reference count that helps Python handle memory.
- `ob_type` encodes the type of the variable.
- `ob_size` specifies the size of the following data members.
- `ob_digit` contains the actual value of the integer. 

The author says that this means storing data in Python takes a bit more memory than just using C. Since python varibles include more information that C variables do, it takes longer to work with them.

The author asks us to consider what is going on when we create [[lists]] in Python. He creates a list as follows, and asks the type.

```python
In [1]: L = list(range(10))
		L
[0,1,2,3,4,5,6,7,8,9]

In [2]: type(L[0])
	
int
```

He says that the ease of creating lists, and being able to put multiple [[data types]] in the same list comes at a memory cost. We can save on the overhead by using fixed-type arrays instead of keeping track of every data type individually.

The book mentions that we can use the built-in `array` type to do this, but we should really be using `ndarray` offered by NumPy since it has better computational abilities. 

The book explains how we can create NumPy arrays from lists by passing `np.array([1,2,3])`. NumPy arrays must be the same [[data]] type, and we can make them multi-dimensional by inserting lists of lists.

The book explains that we can also just make arrays using NumPy routines. We can incorporate some things like the [[normal distribution]] as well. The book gives several examples:

```python
# create a 10-long array of zeroes
np.zeros(10, dtype=int)

# create a 3x5 floating point array of ones
np.ones((3,5), dtype=float)

# create a 3x5 array filled with the number 3.14
np.full((3,5), 3.14)

# create an array filled with a linear sequence that goes from 0 to 20,
# ... stepped by 2
np.arange(0,20,2)

# create an array of five values evenly spaced between 0 and 1
np.linspace(0,1,5)

# create a 3x3 array of uniformly distributed random values between 0 and 1
np.random.random((3,3))

# create a 3x3 array of normally distributed random values with mean of 0
# ... and stdev of 1
np.random.normal(0,1, (3,3))

# create a 3x3 array of random integers between 0 and 10
np.random.randint(0,10,(3,3))

# create a 3x3 identity matrix
np.eye(3)
```

The author asserts that NumPy is the go-to tool for data manipulation in Python. Even other tools like[[Pandas]] tend to be built around NumPy. This section will cover how we can manipulate arrays in NumPy.

The book explains how in a 1-d array, we can just pass `array[0]` to get the first element. In a 2-d array, we need to pass `array[0,0]` to get the first element. We can also modify existing elements in this way, but we should remember that we cannot have mulitple data types in one array.

The author says we can pull multiple values at once, and therefore we may need to *slice* the array and access one within it. We can do this using `array[start:stop:step]` notation. 

According to the book, we can get the first five elements of a single dimensional array by passing `array[:5]`. We could get every other element by passing `array[::2]`, or we could reverse the elements by passing `array[::-1]`. 

The author says that if we want to get the first two rows and first three columns, we could pass `array[:2, :3]`. We can apply all the other notation in the same way we would index a multi-dimensional array. If we want the first column, we can pass `array[:, 0]`. 

The author outlines how we can reshape arrays by using the `reshape` method. This method uses the notation `array.reshape(rows, columns)`. 

The book explains how we can combine and split apart arrays at will. If we want to concatenate two arrays, we can pass `np.concatenate([array1, array2], axis=0)`. This will have the axis set as vertical, so we will default to placing one array above the other if they are 2-d arrays. For 1-d arrays, they will be placed "side-by-side." We can specify `axis=1` if we want 2-d arrays to be put next to each other rather than stacked.

For working with arrays that have more than one dimension, the author continues, we should probably just use `hstack` and `vstack`. `np.hstack` stacks two arrays horizontally (side-by-side) while `np.vstack` stacks them vertically. 

The author says that if we want to split arrays, we can use the `np.split`, `np.hsplit`, and `np.vsplit` functions. For each of these, we pass a list of indices to indicate the split points.

```python
In [1]: x = [1,2,3,99,99,3,2,1]
		x1, x2, x3 = np.split(x, [3,5])
		print(x1, x2, x3)		

[1 2 3] [99 99] [3 2 1]
```

The author draws our attention to the fact that the *n* split points lead to *n+1* subarrays being formed. We can also use the related `np.hsplit` and `np.vsplit` functions.

```python
In [1]: grid =np.arange(16).reshape((4,4))
		grid

array([[ 0,  1, 2,  3],
	   [ 4,  5, 6,  7],
	   [ 8,  9, 10, 11],
	   [12, 13, 14, 15]])		
```

```python
In [2]:	upper, lower = np.vsplit(grid, [2])
		print(upper)
		print(lower)
		
[[0 1 2 3]
 [4 5 6 7]]
[[ 8  9 10 11]
 [12 13 14 15]]		

```

```python
In [3]: left, right = np.hsplit(grid, [2])
		print(left)
		print(right)
		
[[ 0  1]
 [ 4  5]
 [ 8  9]
 [12 13]]
[[ 2  3]
 [ 6  7]
 [10 11]
 [14 15]]
```

## 3.3. Computation on NumPy arrays: universal functions
The author outlines how now we will dive into the reason that we use NumPy so much for [[data science]] - optimized computations. 

The book explains that the fastest way to compute things in NumPy is through the use of *vectorized operations.* We can do this through NumPy's *universal functions,* or ufuncs. 

The author says that Python's default implementation, CPython, does some operations very slowly. This is due to the tradeoffs that Python makes which allow it to be more flexible and easy to use. There have been attempts to mitigate this, such as [[Cython]], which converts Python code to compilable [[C]] code, and the Numba project, which converts Python to LLVM bytecode. 

The book tells us that the sluggishness of Python is most noticeable when small operations are done over and over, such as in [[loops]]. 

The author provides an example. Say we want to take an array of numbers and compute their reciprocal. If we try to do this for an array that contains one million elements, we will see that looping through each one and computing its reciprocal takes almost three seconds. 

```python
def compute_reciprocals(values):
    output = np.empty(len(values))
    for i in range(len(values)):
        output[i] = 1.0 / values[i]
    return output
```

This is absurdly slow when we consider that mobile phones have processing speeds measured in the millions of computations per second. So Python on our beefy computers is basically one-third as fast as the cheapest smartphone's processor. 

The book clarifies the source of this bottleneck. The real issue is the typechecking and function dispatches that CPython does each time the loop repeats. This is a disadvantage of not having a compiled langauge where types are known from the second the code runs. 

The book examines ways around this slowness. There are ways to interface into a static, compiled routine that we can access through NumPy. These operations are called vectorized operations and NumPy will do this automatically. If we pass the following code instead of our previous attempt to find the reciprocals...

```python
print(1.0 / values)
```

... we see that this only takes 4.6 ms to compute one million results. This is nearly four thousand times faster. There are many other applications for vectorized operations in NumPy. 

This is a long section exploring all the functions that NumPy can do in a vectorized format. I'm going to skip this. Just always use NumPy for mathematics.

## 3.4. Aggregations: min, max, and everything in between
This section discusses the fast aggregation functions that we can work on NumPy arrays with. We can just pass `np.sum(L)` where `L` is a NumPy array. NumPy also has variants of the built in `min` and `max` functions that are a lot faster. 

The book explains that if we want to aggregate along a single row or column, we can do that. If we just pass `L.sum()`, the sum will be across the entire array `L`. But if we pass `L.sum(axis=0)`, it will just return an array of values  corresponding to the sums of each column. 

The book lists a lot of other aggregation functions, but the main idea is that if the function exists in built-in Python, NumPy probably has one too. 

## 3.5. Computation on arrays: broadcasting
The author says that *broadcasting* is a set of rules for applying universal functions on arrays of different sizes. For arrays of the same size, binary operations are performed on an element-by-element basis. For arrays of *different* sizes, broadcasting allows operations to still work between them. 

This chapter lists an example. The following code...

```python
a = np.array([1,2,3])
b = np.array([2,4,6])
a + b
```

... will return `array([3,5,9])`. If we pass `a+5`, it will return `array([6,7,8])`. The value of 5 is stretched into an array with length of 3 and then added to `a`. 

The author explains that the situation becomes more complex when we perform broadcasting across both arrays in an operation. 

```python
a = np.arange(3)
b = np.arange(3)[:, np.newaxis]

print(a)
print(b)
```
```
[0 1 2]

[[0]
 [1]
 [2]]
```

If we execute the preceding code, and then pass `a+b`, we will get a new 3x3 array that has broadcasted results from these operations. 

<center>
	<img src='https://jakevdp.github.io/PythonDataScienceHandbook/figures/02.05-broadcasting.png'>
</center>

The author described the three rules of broadcasting. 
1. If two arrays differ in the number of dimensions, the shape of the one with fewer dimensions is padded with ones on it's left side.
2. If the shape of the arrays do not match in any dimension, the array with shape of 1 in that dimension will be stretched to match the other shape.
3. If in any dimension the sizes disagree and neither is equal to one, an error is raised. 

The book goes through a series of examples of how broadcasting works. If we create these arrays...

```python
M = np.ones((2,3))
a = np.arange(3)
```

... we can use these rules to determine if they can work together. The shapes of the arrays are (2,3) and (3,). Because of rule 1, we pad array `a` on the left with ones. Now the shape is `M.shape = (2,3)` and `a.shape = (1,3)`. 

Because of rule two, we see that the first dimension disagrees so we stretch the smaller dimension to match. The shapes are now `M.shape = (2,3)` and `a.shape = (2,3)`. Now these two arrays can be used in binary operations. 

The chapter has a few more examples that I won't go into. 

The book now turns to broadcasting in practice, and says we will see a few situations where broadcasting allows us to speed up our operations. First of all, we can perform array centering.

The author asks us to imagine a situation. If we have a 10x3 array, we could compute the mean of each feature (column) using the `mean` aggregate across the first dimension by passing `X_mean = X.mean(0)`.

Now, the author continues, we can center the array by subtracting the mean by passing `X_centered = X - X_mean`. This is a broadcasting operation. 

## 3.6. Comparisons, masks, and boolean logic
The book introduces this section by saying that we will discuss the use of boolean masks to manipulate NumPy arrays. Masking using booleans is often the most efficient way to accomplish sorting, counting, or filtering data based on a criteria. (see [[booleans and logic]]).

The book asks us to imagine a hypothetical. If we want to count the number of rainy days using a weather dataset, we can first load a dataset of the inches of rainfall:

```python
import numpy as np
import pandas as pd

rainfall = pd.read_csv('data/Seattle2014.csv')['PRCP'].values
inches = rainfall / 245.0 # convert from mm to inches
inches.shape
# > returns (365,)
```

The author explains that this array contains 365 values, giving daily rainfall in inches throughout 2014. We can look at this [[data]] in a histogram, using the following codeblock.

```python
import matplotlib.pyplot as plt
import seaborn; seaborn.set() # setting plot styles

plt.hist(inches, 40);
```

This code block, the author continues, returns a histogram showing that despite Seattle's reputation, most days had a rainfall of zero inches. One way to proceed would be to loop through each observation and increment a timer each time we encounter a day with non-zero rainfall. But that would take a long time, so let's do it another way. 

Instead, the author notes, we can use universal functions from NumPy. If we pass `inches > 0`, NumPy will return an array of true and false booleans. We can then index using this new array. The end result would be the following:

```python
rainy = inches[inches > 0]
print(f'There were {rainy.shape()} rainy days in 2014.')
```

The author reveals that if we want an even more streamlined way to do this, we can just pass `np.count_nonzero(inches)` to get the number of elements greater than zero. 

The book continues towards chaining together multiple logic statements. We can use the `&` symbol and the `|` symbol to chain together these operators. For example, we can find the number of days where rainfall was above 0.5 inches and below one inch:

```python
np.sum((inches > 0.5) & (inches < 1))
```

The author notes that there is a big difference between the `and` and `or` operators on one hand, and the `&` and `|` operators. The former examine the truth or falsehood of the *entire object* while the latter examine each element individually. 

## 3.7. Fancy indexing
...

## 3.8. Sorting arrays
...

## 3.9. Structured data: NumPy's structured arrays
...

# 4. Data manipulation with Pandas
...
## 4.1. Introducing Pandas objects
...

## 4.2. Data indexing and selection
...

## 4.3. Operating on data in Pandas
...

## 4.4. Handling missing data
...

## 4.5. Hierarchical indexing
...

## 4.6. Combining datasets: merge and join
...

## 4.7. Aggregation and grouping
...

## 4.8. Pivot tables
...

## 4.9. Vectorized string operations
...

## 4.10. Working with time series
...

## 4.11. High performance Pandas: eval() and query()
...

## 4.12. Further resources
...

# 5.  Visualization with Matplotlib
...

## 5.1. Simple line plots
...

## 5.2. Simple scatter plots
...

## 5.3. Visualizing errors
...

## 5.4. Density and contour plots
...

## 5.5. Histograms, binnings, and density
...

## 5.6. Customizing plot legends
...

## 5.7. Customizing colorbars
...

## 5.8. Multiple subplots
...

## 5.9. Text and annotation
...

## 5.10. Customizing ticks
...

## 5.11. Customizing Matplotlib: configuration and stylesheets
...

## 5.12. Three-dimensional plotting in Matplotlib
...

## 5.13. Geographic data with Basemap
...

## 5.14. Visualization with Seaborn
...

## 5.15. Further resources
...


# 6. Machine learning
The author begins by stating that [[machine learning]] is the way that data science manifests itself in the [[data science industry]]. This is where the computational and algorithmic skills of data science meet the [[statistics]] of the field, and the result is a collection of approaches to analysis that are focused on effective computation.

The book says that while some treat "machine learning" as a magic bullet, there are strengths and weaknesses of each approach that we should examine. 

The author explains the structure of this chapter. We will dive into the [[Scikit-Learn]] library, introduce the basic concepts of machine learning, and to dive into the details of the most important machine learning approaches. 

## 6.1. What is machine learning?
The author starts off by explaining the definition of machine learning. Some people categorize it as part of AI, but that is not exactly correct. The best way to think about it is as a means of building models of data. The field of ML involves approaches to [[modeling]] relationships from the real world. 

The book explains that "learning" enters our view when we give these models tunable parameters that can be adapted over time to increase the explanatory power of the model. 

The author turns to the different categories of ML. First, [[supervised learning]] involves modeling the relationship between measured features of data and some label or target that is associated with the [[data]]. Once the model is determined, it can be used to apply new labels or predictions to unknown data. This category can be subdivided into [[regression]] and [[classification]] tasks. In classification, the labels are discrete categories, while in regression the labels are continuous quantities.

On the other hand, the author continues, [[unsupervised learning]] involves modeling the features of a dataset without reference to a known label. It is often described as "letting the data speak for itself." These models include [[clustering]] and [[dimension reduction]] tasks. In clustering, we attempt to identify distinct groups of data, while in dimension reduction we attempt to simplify the [[data]] without losing information.

The section turns to some concrete examples of what ML can be used for.

## 6.2. Introducing Scikit-Learn
This section begins by describing the benefits of Scikit-Learn. It's clean, uniform, and streamlined  with good documentation. 

The author says that since ML is all about creating models from data, we should start by looking at how data is represented in Scikit-Learn. Scikit-Learn expects features, $x$, in a matrix where individual features are columns and individual observations are rows. It expects the target vector, $y$, as a one dimensional vector that is the same length as the number of observations in $x$. 

The book now turns to describing the *estimator API.* The API has a few principles that the creators keep in mind. 
1. Consistency. All objects share a similar interface with consistent documentation.
2. Inspection. All specified parameter values are exposed as public attributes.
3. Limited object hierarchy. Only algorithms are represented as classes, datasets are in standard formats, and paramter names use python strings.
4. Composition. Many ML tasks are just sequences of more fundamental algorithms, and Scikit Learn makes use of this.
5. Sensible defaults. 

The book goes through a standard workflow of using the estimator API. First, we choose a class of model to work with. Then we choose model [[hyperparameters]], arrange the [[data]] into a feature matrix and target vector, fit the model to the data, and apply the model to new data. 

The author turns to an example. If we want to perform a simple [[linear regression]], we can do the following:

```python
import numpy as np

# first we create some dummy data to model
rng = np.random.RandomState(42)
x = 10 * rng.rand(50)
y = 2 * x -1 + rng.randn(50)

# now we choose a modle to use
from sklearn.linear_model import LinearRegression

# choose model hypterparameters
model = LinearRegression(fit_intercept=True,
						 n_jobs=1,
						 copy_X=True)

# arrange data into target vector and feature matrix
x = x[:, np.newaxis]

x.shape		# returns (50,1)

# fit the model to training data
model.fit(x,y)

# apply model to new data
model.predict(test_x, test_y)
```

The book goes through some other examples of unsupervised and supervised tasks.

## 6.3. Hyperparameters and model validation
This section first reviews the workflow covered in section 6.2, and then dives into the last two steps, fitting the model to the training [[data]] and testing the model on unseen data. 

...

## 6.4. Feature engineering
...

## 6.5. In depth: naive bayes classification
...

## 6.6. In depth: linear regression
...

## 6.7. In depth: support vector machines
...

## 6.8. In depth: principal component analysis
...

## 6.9. In depth: manifold clustering
...

## 6.10. In depth: k-means clustering
...

## 6.11. In depth: gaussian mixture models
...

## 6.12. In depth: kernel density estimation
...

## 6.13. Application: a face detection pipeline
...

## 6.14. Further machine learning resources
...
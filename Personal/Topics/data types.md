# Data Types
`LINKS:` [[Python]]

---
There are numeric types (int, float, complex), sequence types, set types, and mapping types. They are all used for different purposes and have built-in functionality. 

# Mutable vs Immutable
[[mutability|Mutable]] types can be changed after they are created. Immutable types cannot. Integers are not mutable. When you change a number in Python, you have created a new object in the computer’s memory. 

Lists, sets, and dicts are mutable. When you change them, the computer doesn't gain any new objects in storage. 

# Converting types
We can use `int( )` to convert things to int, etc. Pretty basic.` int( )` will round things down no matter what, so be careful!

`float( )` will do the same for floats. 

# Arithmetic
Pretty natural, except that you have to use `**` to exponentiate instead of the more intuitive ^. 

We can use floor division by using `//`. Floor division rounds to an int. For example, `5//2` = `2`. 

Python follows the usual order of operations. 

There are lots of built in math functions, and we will also introduce even more built-in functions in different [[data science]] libraries. 

`abs(n)` gets the absolute value

`round(n,ndigits)` rounds n to ndigits number of decimal places

# Strings
String assignment can use single quotes, double quotes, or even triple quotes. 

Triple quotes are really only needed if you need to make a string that contains single and double quotes inside of it. 

# Keeping track of variables
We can use the magic command `%whos` to display all the variables that are saved in our Notebook. Using `%whos int` will display all `int` types, etc. 

# Advanced data types
## DefaultDict
The problem with how [[dictionaries]] usually work is that they don't have the ability to add new key values on the fly, you have to input them manually. For example...
```python
count = {}
count['duck']=0

animals = ['duck','duck','duck','goose']

for animal in animals:
	count[animal] += 1
	print(animal)
	
count
```
... this code wouldn't work because `count` has no key value called goose and can't add one to it. 

This is where DefaultDict comes in. If a defaultdict is passed a new key value, it will invent one on the fly and we can preset what it will assume is the starting value for that key. 

```python
from collections import defaultdict

count = defaultdict(int) #here we tell defaultdict to set an int as the type for all new values

animals = ['duck','duck','duck','goose']

for animal in animals:
	count[animal] += 1
	print(animal)
	
count
```

`count` will now set `0` as the starting value of each new key as they are passed into the dict. 

## Named tuple
If we want to create a class that only stores data and are lazy, there's a quick option. The named [[tuples|tuple]] gives us the simplicity of a tuple, but with the labels of a dictionary. 

```python
from collections import namedtuple

Alumni = namedtuple('Alumni','name age gender degree title salary employer')

alice = Alumni(name='Alice',
               age=29,
               gender='F',
               degree ='PhD',
               title = 'Data Scientist',
               salary = 115000,
               employer = 'Thumbtack')
```

## Deque
A deque is designed for easy accessing of data from either side, unlike a list which works best when accesing from the right. 

```python
from collections import deque

d = deque([1,2,3,4])
d.appendleft(3)
d.popright()
```

A deque has built in methods for working with the left or right side, as you can see. 

We can also set a max length for a deque, and it will automatically pop things that move beyond this length. When we add things to the left, it will 'move' the list to the right, removing the rightmost element if the max length has been hit. 

## Generators
These are built in to python. Sometimes we need to reduce the amount of data we're loading into our memory at once. For instance, say we need to calculate what the 1,000,000th prime number is. We don't have to generate a list of primes 1,000,000 numbers long. We can use a generator instead. By using a generator, we could just keep track of one number at a time, increasing it every time we hit a new prime number. 

```python
def generate_numbers():
    """
    An infinite number generator
    """
    x = 0
    while True:
        x += 1
        yield x # instead of return, I use yield, which makes this into a generator!
        
        
my_generator = generate_numbers()
for iteration in range(10):
    next_number = next(my_generator)
    print(next_number)
```

Generators are vital when we're working with big data that your computer, and in some cases no computer on earth, could have in memory all at once. 

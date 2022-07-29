---
author: 
rating: WIP 
genre: STEM
format: article
---
# Python Object Oriented Programming (2021)
`LINKS:` [source](https://www.programiz.com/python-programming/object-oriented-programming)
#article
`AUTHOR:` N/A

---
# Object oriented programming
The article begins by discussing the place that [[OOP]] has in [[Python]]. Python is a *multi-paradigm* programming languages, meaning that there are multiple possible approaches. 

The author says that OOP is one of the popular approaches to solving programming problems. Objects have two characteristsics: attributes and behavior. For example, a parrot is an object, and it has the following properties:

- name, age, color as *attributes*
- singing, dancing as *behavior*

The author underlines the importance of using OOP for [[Don't repeat yourself when coding]]. DRY stands for Don't Repeat Yourself, and is a good mantra for programmers. 

# Class
The article says that a *class* is a blueprint for an object. For example, we can create a `Parrot` class.

```python
class Parrot:
	pass
```

# Object
An object, the article continues, is a specific instance of a class. If we want to create a specific parrot, we have to pass `my_parrot = Parrot()`. 

## Example 1: creating class and object in Python
```python
class Parrot:
	# class attribute
	species = 'bird'
	
	# instance attribute
	def __init__(self, name, age):
		self.name = name
		self.age = age
		
# instantiate the parrot class
blu = Parrot('Blu', 10)
woo = Parrot('Woo', 15)

# access the class attributes
print(f'Blu is a {blu.__class__.species}')

# access the instance attributes
print(f'{blu.name} is {blu.age} years old')
```

The author notes that we can access class attributes by passing `__class__.<attribute>`.

# Methods
The author says that methods are functions defined inside the body of a class. They define the behaviors of the object.

## Example 2: creating methods in Python
```python
class Parrot:
	
	# instance attributes
	def __init__(self, name, age):
		self.name = name
		self.age = age
		
	# instance method
	def sing(self, song):
		return f'{self.name} sings "{song}".'
	
	def dance(self):
		return f'{self.name} is now dancing.'
	
# instantiate the object
blu = Parrot('Blu', 10)

# call our instance methods
print(blu.sing('Happy'))

>>> Blu sings "Happy"
```

# Inheritance
The article covers how inheritance can allow us to create a new class using details from an existing class. This creates a child class that we can add to from the parent class' code base.

## Example 3: use of inheritance in Python
```python
# parent class
class Bird:
	
	def __init__(self):
		print('Bird is ready.')
		
	def who_is_this(self):
		print('Bird.')
		
	def swim(self):
		print('Bird is swimming.')
		
# child class
class Penguin(Bird):
	
	def __init__(self):
		# call super() function
		super().__init__()
		print('Penguin is ready.')
		
	def who_is_this(self):
		print('Penguin.')
		
	def run(self):
		print('Penguin is running.')
```

In the above code, the article explains, we have created a `Bird` parent class and a `Penguin` child class that contains all the methods of `Bird` and has some additional ones.

# Encapsulation
Using OOP, the author says, we can restrict access to methods and varibles in order to prevent direct modification. This is called *encapsulation.* We denote private attributes using underscores as prefix.

## Example 4: data encapsulation in Python
```python
class Computer:
	
	def __init__(self):
		self.__maxprice  = 900
		
	def sell(self):
		print(f'Selling price: {self.__maxprice}')
		
	def set_max_price(self, price):
		self.__maxprice = price
		
c = Computer()
c.sell()

>>> Selling price: 900

# change the price
c.__maxprice = 1000
c.sell()

>>> Selling price: 900	# note that this did not change to 1000
	
c.set_max_price(1000)
c.sell()

>>> Selling price: 1000	# note that this is now changed
```

# Polymorphism
The article explains that polymorphism allows us to use a common interface for many [[data]] types. 

## Example 5: polymorphism in Python
```python
class Parrot:
	
	def fly(self):
		print('Parrot can fly.')
		
class Penguin:
	
	def fly(self):
		print('Penguin cannot fly.')
		
# common interface
def fly_test(bird):
	bird.fly()
	
# instantiate objects
blu = Penguin()
sally = Parrot()

fly_test(blu)

>>> Penguin cannot fly.

fly_test(sally)

>>> Parrot can fly.

```
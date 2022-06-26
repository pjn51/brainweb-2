---

---
# Python objects can inherit attributes. 
In [[Python]], when we create [[OOP|classes]], we don't have to start from scratch. Let's say we have a class like such:

```python
class Animan():
	def __init__(self):
		print('Animal created')
	def run():
		print('Pitter patter')
```

We can create another class:

```python
class Cat(Animal):
	def __init__(self):
		Animal.__init__(self)
```

Now, if we pass `my_cat = Cat()` and then pass `my_cat.run()`, it will print  `Pitter patter`.  

---
#idea/compsci/python 
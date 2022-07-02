---

---
# Python objects can use special methods. 
In [[Python]], our [[OOP|classes]] can alter the output of things like `len()` and `print()`. 

```python
class Book(self):
	def__init__(self, title, author, pages):
		self.title = title
		self.pages = pages

	def __str__(self):
		return f'{self.title} by {self.author}'

	def __len__(self):
		return self.pages
```

```python
> my_book = Book('Capital', 'Karl Marx', 999)
> print(my_book)

'Capital by Karl Marx'

> len(my_book)

999
```

---
#idea/compsci/python 
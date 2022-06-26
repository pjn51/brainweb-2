# Comprehensions
`TAGS:`

---
# Introduction
Comprehension is another way to manipulate sequential data and iterables. It’s a very fast way to create [[lists]] and things like that in [[Python]]. 

```python
My_list = [1,2,3,4 ]
My_list_squared = [ num**2 for num in my_list]
```

The above syntax is more efficient and faster than creating a `for` loop to square the elements in the initial list. This is called a list comprehension. 

We can also use logic to filter lists in this way. 

```python
My_list_even = [ num for num in my_list if num % 2 == 0]
```
# Copying

---
In [[Python]], the variable doesn't really contain the value in question. 

## Problems with copying variables
```python
a = [1,2,3]
b = a
b
```

This will return `[1,2,3]` as we would expect. 

```python
a.append(9)
b
```

This will return `[1,2,3,9]` which isn't what we want!

## What's going on here?
Python variables function by assigning labels to values in the memory of the computer. When we say `a = [1,2,3]`, we create `[1,2,3]` in the memory, and we have the variable `a` pointing to it. When we say that `b = a`, we are making a new label pointing to that same `[1,2,3]`. 

To solve the above issue, we can pass...

```python
a = [1,2,3]
b = list(a)
```

This is telling the computer to create a new list for `b` with the contents of `a` inside of it, solving the above issue. 

# Nested lists
Ok, so we've solved the issue, right? What if we pass this...

```python
a = [1,2,[3,4],5]
b = list(a)
a[2][0] = 999
b
```

What! This returns `[1,2,[999,4],5]`. What happened???

When we said that `b = list(a)`, this created a new list with the contents of `a` inside of it. Unfortunatley, `a` had another list inside of it, `[3,4]`. And *this* list is still shared between `a` and `b`. Damn!

This is known as a *shallow copy* for this reason. 

# Deepcopy
From the `copy` module, `deepcopy` is designed to save us from this issue. 

```python
from copy import deepcopy
a = [1,2,[3,4],5]
b = deepcopy(a)
```

`deepcopy` will create a totally new memory item for `b` so that we don't get fucked up.

We only have to use `deepcopy` with nested items. For everything else, we can use `copy` or something. 
# Mutability
`LINKS:` [Medium article on this concept](https://medium.com/@meghamohan/mutable-and-immutable-side-of-python-c2145cf72747#:~:text=Everything%20in%20Python%20is%20an%20object.&text=Simple%20put%2C%20a%20mutable%20object,Custom%20classes%20are%20generally%20mutable.)

---
# What does it mean for something to be mutable?
First of all, everything in python is an [[OOP|object]]. This means that it has an object instance in memory. 

When an object is initiated, it gains a unique object id, and is assigned a type. This type cannot be changed.

We can see this unique id by using the built-in function, `id()`. If we want to see the type, use `type()`. 

Object|Status
---|---
List|Mutable
Dict|Mutable
Set|Mutable
Int|Immutable
Float|Immutable
Str|Immutable
Tuple|Immutable

## A note on immutable collections
An immutable collection of other objects, such as a tuple, isn't *really really* immutable. This is because while the tuple's contents can't be changed, it's just the *bindings* inside the tuple that are unchangeable. 
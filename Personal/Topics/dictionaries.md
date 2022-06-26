# Dictionaries
`LINKS:` [[Python]]

---

Dictionaries are a [[data types|data type]] in python.

These use the same syntax as sets, but have key values. Dictionaries are mutable. They are used to store collections of key value pairs. The key is a descriptor, and the value is what is described. While the values are mutable, the keys are not. 

There are multiple ways to create dicts, Python is quite flexible and this will help when we work with functions. 

Dictionaries can contain multiple data types. For instance, we can have a dict where the values are lists, int, strings, or even other dictionaries. 

We use keys to access values, instead of indexing. For instance, if we want to get the first element in a dict, using `my_dict[0]` wouldn't work, but using the name of the first key instead of zero would work. In the case of a list within a dict, we can use the standard nested indexing notation. If a dict is in a dict, repeat that key name for the nested dictionary as if it was the index position in a list. 

# Dictionary methods
`.keys( )` this returns a display of all the keys in a given dictionary. 
`.items( )` this returns a display of all the values in a dict. 
`.new( )` adds a given new set of value key pairs to a dict. 
`.pop(key)` removes the key given. 

Membership test operations can only be performed on keys, not on values. 

# Updating elements
We can update values in a similar way to updating a list element. 

We can add new key value pairs to the end by calling `my_dict[‘newkey’] = ‘newval’`

We cannot change the names of the keys. 

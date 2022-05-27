# Strings
`TAGS:` 

---
Strings are a [[data types|data type]] (in [[python]]) similar to lists in their methods and how to manipulate them. However, they are immutable. We can still perform type conversions and index and slice them in the same way as we did for lists. 

## String Operations
We can do membership test operations just like with lists. 

We can repeat strings (EX: `string_1 = ‘abc’ ; print(string_1*2)` will return `abcabc`

We can use the `sort` method on a string. This will put the string in alphabetical order, transforming it into a list. 

The `.lower()` and `.upper()` methods will put the string into lowercase or uppercase. This is useful for input validation simplification. 

Python also assigns values to rank each letter. This means we can use min and max on strings. 

The `split` method is another useful one. This will split a longer string into a list of smaller ones, with the default delimiter being whitespace. But you can specify your own delimiter such as a comma or something. 

The `join` function is the opposite of the split method basically. 

## Formatting strings
In order to put variable information into a string, you can use the `.format` method. 

```python
print(‘My favorite color is { }’.format(color)
# or
print(f"My favorite color is {color}")
```

This will insert whatever you have as the value of the variable color. 

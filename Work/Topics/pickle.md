# Pickle 🥒
`TAGS:`
---

This is a tool for saving [[data]] for later in [[Python]]. 

It works by creating a binary file, writing our object to that file, and then storing it away in our computer for later. When we want to use it, we can unpack it into python again. Let's see an example. 

Say we have an object called `mydata`. It's a bulky python object that we won't have to use for a while but want to keep safe.

```python
import pickle

with open('mydata.pickle','wb') as to_write:
	pickle.dump(mydata, to_write)
```
In the above code, `wb` means write-binary mode. 

After we run this, we can safely remove `mydata` from our python environment and it will be kept safe for later. 

When we want to open it, we say...
```python
with open('mydata.pickle', 'rb') as read_file:
	revived_data = pickle.load(read_file)
```
This puts us into read-binary mode (`rb`), and creates a new object called `revived_data` that has all the info from `mydata`. 

# How to use pickle
It's a great way to set checkpoints for local work. When you get the data, pickle it and open a new notebook for analysis. When you're done analyzing it, take your results and pickle them. Put them in a new notebook for visualization. 
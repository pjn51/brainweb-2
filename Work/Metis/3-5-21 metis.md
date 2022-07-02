 # Metis Notes for Friday, March 5th
`LINKS:` [[metis week 9]]
`TAGS:` #meeting/career

---
## Pair: map-reduce

**Problem 1**: perform a list comprehension that takes the square of each element in a list, and then keeps the odd ones. 
```python
numbers = range(1,101)

odd_squares = [num**2 for num in numbers if num**2 % 2 != 0]
```

**Problem 2**: repeat the first problem using the `map` and `filter` functions. 
```python
squares = list(map(lambda x: x**2, numbers))
odd_squares = list(filter(lambda x: x % 2 != 0, squares))
```

**Problem 3**: use `reduce` to calculate the sum of a list of numbers 1-100. 
```python
reduce(lambda x, y: x+y, numbers)
```

**Problem 4**: use reduce to find the max of a random list of numbers.
```python
numbers_r = [4, 2, 67, 2, 98, 56, 43, 24, 91]

def my_max(x):
	if x > y:
		return x
	else:
		return y

reduce(lambda x, y: my_max(x, y), numbers_r)
```

## Lecture - [[distributed file system]]
- There is a lot that goes on behind the scenes with this stuff. 
- People make a lot of money for their knowledge on this stuff. 
- This is just a review of the basic idea of what's happening so that we have an intuition about what's going on in the background.
- This isn't meant to be a comprehensive study of these systems. 

### Intuition
- So far, we've just pulled the [[data]] into RAM and worked on it there. 
- But what if we are trying to use a dataset that is larger than the amount of RAM that we have?
- We need a system that can handle all this.
- We *partition* the data between multiple machines so that each partition can be managed by wherever it is. 
- We have to assign a *manager* to manage the whole partition system, and multiple *workers* to work in each partition to perform operations and stuff. 
- Nodes
	- There is a single *name node* and multiple *data nodes*
	- Name node
		- Controls where the data lives, can access the data, stores [[metadata]] about the other nodes and partitions
	- Data node
		- Stores the data and listens to the name node
- Distributed File System
	- [[Hadoop]] was the first framework to implement this system
	- There are also *redundancies* built in, so that unreliable data systems could be preserved. 

### How Does it Work?
- We have a person accessing the cluster
- They access through the ==manager node==. 
- After the manager node accesses all the data nodes we want, everything gets backed up
- If there's data we want to add to the cluster, we do so through the name node. We break the data into partitions, and then move the data into various nodes that also have redundancies built in. 

### Map Reduce
- Now we have data stored in these nodes. How do we work with this data?
- One option would be to pull all the data and just work on it. There's a bottleneck with this. We lose redundancy and there's only one point of contact for the calculations. That might be too much for a single computer to handle.
- The idea behind mapreduce is to use the cluster to do the work for us. 
- If we want to take the average of a gigantic list or array, we could break up the data into the partitions, and tell each partition to find the average of itself. This is the `map` stage of the process. Then we could take the average of the average of all partitions. This is the `reduce` step. This is a lot faster because there are more calculations happening at the same time. (parallellization)
- Basically, map-reduce breaks a big problem into a bunch of little problems. It works with anything that can be parallelized, like counting, filtering, some types of minimization, etc

## Lecture - [[Spark]]
- Spark uses the ideas of [[distributed file system]] in order to help us work faster. 
- Why is spark fast?
	- It uses a really good project manager
	- It uses RAM whenever possible instead of storage
- Directed acyclic graphs (DAGs)
	- These are the project managers
	- If you give spark a task with 60 steps, it will create a DAG to map out the most efficient possible way to do all those steps. Then it will execute the plan. 
	- They can make sure all possible parallelization is happening, and that RAM is used as efficiently as possible. 
- Resilient distributed datasets (RDDs)
	- The backbone of spark
	- Dataset is split into partitions
	- Immutable (see [[mutability]])
- Spark API
	- Uses [[lazy evaluation]] (comes up with instructions before starting any operations)
	- Two kinds of behaviors- transformations and actions
		- Transformations prepare data, actions do calculations
		- `map` is a transformation, `reduce` is an action

## Lecture - [[google colab]]
- This service can really speed up our training by giving us access to GPUs and more processing power. 
- With the free version, we can get 12 hour runtimes. If we're training a project that takes more than 12 hours, we need to break up the training into chunks of 12 hours each. 
- With the pro version which is $10 per month, we can get 24 hour runtimes and fewer timeouts. 
- Connect to Google Drive
	- We can't store files in colab for longer than our session, so don't leave anything important in there. 
- We can run google colab cells in the same way that [[Jupyter Notebook]] works. 
- GPU vs CPU
	- GPUs are a lot faster than just a CPU alone. 

## Going over the [[deep learning]] test
The likelihood that a NN will overfit is dependent on the size of the training data. As we add training data to the dataset, we will decrease the risk of overfitting. 
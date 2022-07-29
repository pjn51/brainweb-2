---
author: Bradshaw, Brazil, Chodorow
genre: STEM
---
# MongoDB - The Definitive Guide (2020)
`SOURCE:` https://learning-oreilly-com.ezproxy.spl.org/library/view/mongodb-the-definitive/9781491954454/preface01.html#sect2_d1e227
#wip #book 

---
1. Introduction to MongoDB
2. Getting started
3. Creating, updating, and deleting documents
4. Querying
5. Indexes
6. Special index and collection types
7. Introduction to the aggregation framework
8. Transactions
9. Application design
10. Setting up a replica set
11. Components of a replica set
12. Connecting to a replica set from your application
13. Administration
14. Introduction to sharding
15. Configuring sharding
16. Choosing a shard key
17. Sharding administration
18. Seeing what your application is doing
19. An introduction to MongoDB security
20. Durability
21. Setting up MongoDB in production
22. Monitoring MongoDB
23. Making backups
24. Deploying MongoDB

---
# 1. Introduction to MongoDB
The authors introduce [[MongoDB]] as a powerful, flexible, and scalable [[database]]. They say that this chapter will discuss the various decisions that were made during the creation of MongoDB. They note that MongoDB is *not* a relational database like [[SQL]], and that instead, [[MongoDB is document-based]]. They say that this allows for the representation of complex hierarchical relationships within *documents* rather than *rows.* They say that this is more scalable as well. 

Overall, I'm reading this book to answer the question of "[[How does MongoDB work?]]"

# 2. Getting started
The authors further explain how [[MongoDB is document-based]], and elaborate that [[MongoDB organizes documents into collections]]. While we don't technically have to have multiple collections, the authors recommend it to ease the development and querying process. 

While documents have a dynamic schema ([[Schema defines database structure]]), the authors recommend creating consistent ones for ease of use. 

While they have no literal connection, the authors explain that many choose to use a *subcollection* organizing principle, where commections related to a parent collection will use the naming convention `parent.child`. For example, if you had sales data, and you also had [[metadata]] about those sales, the metadata could live in a collection called `sales.metadata`. 

The authors say that [[MongoDB organizes collections into databases]]. They argue that we should keep all data for one application in the same database. 

The authors explain that [[MongoDB is accessible via command line]]. We pass `mongo` to start the shell. The authors say that this is a full featured [[JavaScript]] interpreter, so we can run any JS program within it. We can see what database we're currently connected to by passing `db`. We switch databases by passing `use` and then the name of the database we want to move into. 

I'm going to move on to the next section, but this section also contains useful information about working in the shell. 

# 3. Creating, updating, and deleting documents
I'm going to skip this section for now. 

# 4. Querying
The authors explain that the `find` method is essential to querying MongoDB. It returns a subset of documents in a collection. 

```js
// return whole 'users' collection
db.users.find()    

// return docs within 'users' that have 'age' = 30
db.users.find({'age': 30})    

// return docs that have age:30 AND name:Joe
db.users.find({'age': 30,
			   'name': 'John'})

// return the name of all docs with age: 30
db.users.find({'age': 30}, 
              {'name': 1})
```

Note that in the last command, we have two parameters for `find`. The second parameter is a key value pair of the value we want to return. If we make that key equal to one, it will be returned, and if we make it equal to zero it won't be returned. 
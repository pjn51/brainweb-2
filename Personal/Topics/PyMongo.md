# PyMongo
`LINKS:` [documentation](https://pymongo.readthedocs.io/en/stable/)
`TAGS`: 

---
# Introduction
PyMongo is a [[Python]] distribution used for working with [[MongoDB]]. 

# Importing and connecting
Of course, we have to `import pymongo`. We also have to have a MongoDB instance running on the default host and port. We can start this like so:

```
$ mongod
```

In order to make a connection, we need MongoClient.

```python
from pymongo import MongoClient
client = MongoClient()
```

This above code will connect the client on the default host and port. If we want to, we can specify the host and port specifically like this:

```python
client = MongoClient('localhost', 27017)
# alternatively...
client = MongoClient('mongodb://localhost:27017/')
```

# Getting a database
A single instance of MongoDB can support multiple [[database|databases]]. We can access databases using attribute style access on MongoClient instances, where `test_database` is what we want to access:

```python
db = client.test_database
# alternatively...
db = client['test_database']
```

# Getting a collection
We can get a collection in a similar way:

```python
collection = client.test_collection
# alternatively...
collection = client['test_collection']
```

# Reading MongoDB collections into pandas
In order to hook MongoDB stuff up to [[Pandas]], we can use these functions...

```python
def _connect_mongo(host, port, username, password, db):
    """ A util for making a connection to mongo """

    if username and password:
        mongo_uri = 'mongodb://%s:%s@%s:%s/%s' % (username, password, host, port, db)
        conn = MongoClient(mongo_uri)
    else:
        conn = MongoClient(host, port)

    return conn[db]

def read_mongo(db, collection, query={}, host='127.0.0.1', port=29438, username=None, password=None, no_id=True):
    """ Read from Mongo and Store into DataFrame """

    # Connect to MongoDB
    db = _connect_mongo(host=host, port=port, username=username, password=password, db=db)

    # Make a query to the specific DB and Collection
    cursor = db[collection].find(query)

    # Expand the cursor and construct the DataFrame
    df =  pd.DataFrame(list(cursor))

    # Delete the _id
    if no_id:
        del df['_id']

    return df
```

Note that these functions are using the host and port of the stashlogix server, since I'm currently working on the [[stash-o-matic project]] project.
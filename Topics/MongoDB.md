# MongoDB
`LINKS`: [[noSQL]] | [docs](https://docs.mongodb.com/manual/introduction/)
`TAGS`: 

---
A record in MongoDB is called a *document.* It is a data structure composed of key value pairs. 

```
{
	name: "Patrick",
	age: 23,
	status: "cool"
	ideas: ['code','have fun']
}
```

MongoDB stores documents in *collections,* which are like tables in [[RDBMS]]. 

## Getting started
Within a MongoDB shell, we can type `db` to display the current [[database]]. If we want to switch to a new [[database]], we can type `use <db>` where we input the name of the desired database.

## Databases and collections
[[MongoDB is non-relational]]. 

If we want to create a new database, we can do so from within a mongo shell. 

```
use new_db

db.myNewCollection1.insertOne( {x:1} )
```

The above command will create a new database called `new_db`, create a new collection within it called `myNewCollection1`, and insert a document into that collection.

## Views
A MongoDB *view* is a queryable object whose contents are determined by a [[MongoDB aggregation pipeline]]. For example, we could create a view on a collection of employee data that excludes personal information. Then, we could allow a website to have access to this view. 

We can create views that join multiple databases together, or ones that create new metrics using available data. 

If we want to create a view, we can pass the command a couple different ways. We could use the `createCollection()` method:

```
db.createCollection(
	'<viewname>',
	{
		'viewOn': '<source>',
		'pipeline': [ <pipeline> ],
		'collation': { <collation> }
	}
)
```

We could also use the `createView()` method:

```
db.createView(
  "<viewName>",
  "<source>",
  [<pipeline>],
  {
    "collation" : { <collation> }
  }
)
```

Remember, we must create views in the same database as the source collection. 

## View behavior
Views are read-only. There are lots of read operations we can apply to views:

- `db.collection.find()`
- `db.collection.findOne()`
- `db.collection.aggregate()`
- `db.collection.countDocuments()`
- `db.collection.estimateDocumentCount()`
- `db.collection.count()`
- `db.collection.distinct()`
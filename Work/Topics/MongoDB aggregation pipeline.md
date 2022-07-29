# MongoDB Aggregation Pipeline


---
# Introduction
This is basically an *aggregation pipeline* on other collections or views in [[MongoDB]]. An aggregation pipeline is basically a data processing pipeline within MongoDB. For example, an aggregation pipeline might be something like this:

```mongodb
db.orders.aggregate([
	{ $match: {status:'A'} },
	{ $group: (_id: '$customer_id', total: {$sum: '$amount'} ) }
])
```

Above, the first stage in the pipeline is the `$match` stage. We filter the documents by the `status` field and pass those that have a status of "A" down to the next phase. The second step is the `$group` phase. We group the documents by the `customer_id` field and calculate the sum of the amount for each customer id.
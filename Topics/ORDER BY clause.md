---
aliases: 
---
# ORDER BY clause
---
In [[SQL]], the `ORDER BY` clause is usually found in a [[SELECT statement]]. It determines the order in which the result set is sorted. 

Note that by default, this will order in ascending, but we can specify either using `asc` and `desc` [1]. 

When performing set operations, make sure to `order by` a column found in the *first* table that is used [2]. 

---
1. [[Learning SQL (2009)]], p57
2. Ibid, p108
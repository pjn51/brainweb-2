---
aliases: 
---
# WHERE clause
---
In [[SQL]], `WHERE` is a very common clause that can be a part of all SQL data statements aside from `INSERT`. It's a filtering clause similar to the [[HAVING clause]], but [[In SQL, WHERE filters rows, HAVING filters groups]]. 

```sql
select name, birthday
from employees
where department = 'sales';
```

The `WHERE` clause above will remove all rows where the employee isn't associated with the sales department. 

Above, `department = 'sales'` is referred to as a *condition.* We can apply one or more conditions to the `WHERE` clause, which can be equality conditions, such as the example above, but they can also perform bucketing, where we specify that a column must be `between` two values. We do this using an `AND` operator.  We can check for set membership via `IN`, and look for a pattern using wildcards or [[regex]] with `LIKE`. 

---
[1]: [[Learning SQL (2009)]], p66-70
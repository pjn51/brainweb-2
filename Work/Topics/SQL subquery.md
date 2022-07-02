---
aliases: [SQL subqueries]
---
# SQL subquery
---
[[SQL subqueries allow multi-stage operation]]. We plug these into the [[FROM clause]] like so:

```sql
select max(sub.column_one)
from (
	select avg(column_three) as column_one
	from my_table
) as sub;
```

Note that we *must* assign an alias to subqueries.

Furthermore, [[SQL subqueries can speed things up]]. 

---
1. https://mode.com/sql-tutorial/sql-sub-queries/
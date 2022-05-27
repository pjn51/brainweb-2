---
aliases: [sql window function, window function, windown functions, ]
---
# SQL Window Functions
---
Sometimes in [[SQL]], we want to calculate a value using multiple rows without combining those rows. We can use a *window function,* because [[SQL window functions operate without aggregating]]. 

A simple example would be a running total. For this example, we are finding the running total of usage time for a bikeshare program.

```sql
SELECT duration_seconds,
	SUM(duration_seconds) OVER (ORDER BY start_time)
	AS running_total
FROM tutorial.dc_bikeshare_q1_2012;
```

The above code creates an aggregation, called `running_total` without grouping by anything. 

Note that we *cannot* include window functions in a [[GROUP BY clause]]. 

---
[1]: https://mode.com/sql-tutorial/sql-window-functions/
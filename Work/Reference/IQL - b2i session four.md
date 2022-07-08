---
origin: 2022-07-06
aliases: []
---
# IQL - b2i session four
---
> [!intro]
> This is the fourth session of [[IQL - From Beginner to Intermediate]].

In this session, we had a brief HAVING recap, reviewing that it's basically WHERE for something already grouped.

The below query doesn't work.
```sql
FROM joblevelmoderation yesterday today
WHERE count() > 100
GROUP BY username
SELECT
```

Instead, we have to use HAVING:
```sql
FROM joblevelmoderation yesterday today
WHERE
GROUP BY username HAVING count() > 100
SELECT
```

We also covered [[regex]] in [[IQL]], and the instructor noted that it's very CPU intensive.

---

---
origin: 2022-07-11
aliases: []
---
# IQL - b2i session five
---
> [!info]
> This is the fifth session of [[IQL - From Beginner to Intermediate]].
We went over the ho

We went over the homework as usual. Then we discussed [[regex]] further, and he outlined the regex for getting a case-insensitive phrase search: `".*[Pp][Hh][Rr][Aa][Ss][Ee].*"` 

Then we discussed how to alias and why we would do that. We can rename columns by passing `SELECT answer as ans` for example. We might want to do this in order to query multiple [[IQL indices]] or rename variables for ease of presentation.

## Homework
1. For the English queue, show a breakdown of volume between the different origins day over day over from January 1st, 2021 to February 1st 2021.

```sql
FROM joblevelmoderation 2021-01-01 2022-02-02
WHERE queue = 'Job_Level_Moderation'
GROUP BY origin, time(1d)
SELECT
```

2. Present the dockeys for jobs that were marked badjob on July 24th 2020, by the most active moderator on that day (the moderator who completed the highest volume)(This is a two part)

```sql
FROM joblevelmoderation 2020-07-24 2020-07-25
WHERE answer = 'badjob' username in 
	(FROM joblevelmoderation 2020-07-24 2020-07-25
     WHERE
	 GROUP BY username[1])
GROUP BY dockey
SELECT
```

3. If we wanted to message the Quality Investigations team 3 companies that they should take a deeper look at, what would be your recommendations based on JLM data for the month of August 2020.

```sql

```

4. Which queue has the highest badjob percentage for their keyword origin based on the month of July 2020?

```sql
FROM joblevelmoderation 2020-07-01 2020-08-01
WHERE origin='keyword'
GROUP BY queue
SELECT answer='badjob'/count()
```

5. For the English queue, what origin had the most jobs in job alert or organic before the jobs went into moderation in August 2020?

```sql
FROM joblevelmoderation 2020-08-01 2020-09-01
WHERE queue="Job_Level_Moderation"
GROUP BY visibility_at_queue
SELECT 
```

6. For jobs that went into moderation in JA or Organic in August 2020, what policy most often landed them in lowered visibility?

```sql
FROM joblevelmoderation 2020-08-01 2020-09-01
WHERE visibility_at_queue IN ("Job Alert", "Organic")
GROUP BY waldorulestok
SELECT 
```
---
origin: 2022-07-01
aliases: []
---
# IQL - b2i session two
---
> [!summary]
> This is the second session of [[IQL - From Beginner to Intermediate]].

In this session, we went over the homework before diving into a discussion on LIMIT and SELECT, as well as how to use multiple parameters within statements. 

For question 2 on the first set, I answered slightly wrong. My answer:

```sql
FROM joblevelmoderation 2020-01-01 2020-02-01
WHERE job_country_code = 'IN'
GROUP BY answerclassifications[5]
SELECT --defaults to count()
```

Correct answer: 

```sql
FROM joblevelmoderation 2020-01-01 2020-02-01
WHERE queue = 'Job_Level_Moderation_IN' 
GROUP BY answerclassificationstok[5]
SELECT --defaults to count()
```

This was just slightly off, based on a misunderstanding of the fields.

As for LIMIT, we can add a bracket to `GROUP BY` in order to only pull $n$ results: `GROUP BY field[n]`. This defaults to `[TOP n]` but we could also specify `[BOTTOM n]` if we want.

SELECT defaults to `count()` of something, depending on the index that we're using:

- `joblevelmoderation` - count of doc keys
- `mechaactions` - count of actions
- `searchablejobs` - count of jobs
- and so on.

We can also perform basic math in the SELECT statement. If we want to find the percentage of jobs in a JLM queue labeled as bad, we can do so:

```sql
FROM joblevelmoderation yesterday today
WHERE 
GROUP BY 
SELECT answer = 'badjob' / count()
```

Finally, we can have multiple parameters per statement: `WHERE queue in ('queue_a', 'queue_b')`. 

## Homework
1. What moderators [top 5] selected Low Quality Title the most often in the month of July of 2021?

```sql
FROM joblevelmoderation 2021-07-01 2021-08-01
WHERE answerclassificationstok = 'GP_P_lowQualityTitle'
GROUP BY username[5]
SELECT 
```

2. What waldo rules [top 10] hit the most jobs from the Random Origin in the English queue in July of 2021?

```sql
FROM joblevelmoderation 2021-07-01 2021-08-01
WHERE queue = 'Job_Level_Moderation' origin = 'rand'
GROUP BY waldorulestok[10]
SELECT 
```

3. Show the day over day changes in good jobs and bad job decisions over the last month for the English queue

```sql
FROM joblevelmoderation 2022-06-01 today
WHERE queue = 'Job_Level_Moderation' origin = 'rand' 
GROUP BY yyyymmdd
SELECT answer = 'badjob' / count() * 100
```

4. What origin in the English queue has the highest ratio of bad jobs in the month of August?

```sql
FROM joblevelmoderation 2021-08-01 2021-09-01
WHERE queue = 'Job_Level_Moderation' 
GROUP BY origin
SELECT answer = 'badjob' / count() * 100
```

Note: it seems like when I try to narrow to one result by grouping by `origin[1]`, it changes the answer.

5. In the month of August, what feedids [top 3] have the lowest ratio of bad jobs (Or conversely, highest ratio of good jobs?). In other words, what feeds had the lowest rate of jobs that were given the answer badjob?

```sql
FROM joblevelmoderation 2021-08-01 2021-09-01
WHERE queue = 'Job_Level_Moderation' 
GROUP BY job_feed_id[3]
SELECT answer!= 'badjob' / count() * 100
```

---
1. [Course worksheet](https://docs.google.com/document/d/1QbP4A4yuJv3gLm7A-FilTJfdP0ADSWo8RzySDitO-KA/edit)
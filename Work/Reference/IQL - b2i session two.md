---
origin: 2022-07-01
aliases: []
---
# IQL - b2i session two
---
> [!summary]
> This is the second session of [[IQL - From Beginner to Intermediate]].

- HW review
	- 2: where should have been `queue='Job_Level_Moderation = 'IN'` and GROUP BY `answerclassificationstok[5]`
- LIMIT / SELECT stuff
	- We can add a bracket to GROUP BY: `GROUP BY answer[n]` where $n$ is the number of results. 
	- SELECT defaults to count of something dependent on index
		- joblevelmoderation -> dockeys
		- mechaactions -> actions
		- searchablejobs -> jobs
		- jobreportfraud -> job reports
		- etc
	- We can perform ratios and percentages in the select statement
		- `select answer = 'badjob' / count()` gets percentage labeled as bad within joblevelmoderation
- Multi param
	- `WHERE queue IN ('queue_a', 'queue_b')`

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
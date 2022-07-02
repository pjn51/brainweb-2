---
origin: 2022-06-30
aliases: []
---
# IQL - Beginner to Intermediate; session one
---
> [!summary]
> This is the first session of [[IQL - From Beginner to Intermediate]]

## Recording notes
At the start of this meeting, we went over the syllabus and the structure of the course. There are going to be eight meetings, each will be 45 minutes, and all will have a homework assignment that should take 30 or 40 minutes to finish.

We went over the basics of [[IQL]], how it was [[internal Indeed tools|built by Indeed]], and talked about the benefits of knowing it. 

Basically, IQL has four clauses: FROM, WHERE, GROUP BY, and SELECT. It appears as an inverted [[SQL]] statement. In SQL, SELECT comes first, but here it comes last. 

## FROM
The standard FROM clause in IQL is in the form `FROM {index name} {first date} {end date}`. For example, we might be getting [[data]] from the JLM dataset between in January 2020: `FROM joblevelmoderation 2020-01-01 2020-02-01`. ==Note that the end date is exclusive in this syntax, because of the way that data refreshes. Also note that all IQL timestamps are in Central Time.==

## WHERE
This is exactly the same as the SQL [[WHERE clause]]. It filters the data. 

## GROUP BY
This is also the same as the SQL [[GROUP BY clause]]. If we don't pass anything for this clause, it will return the total for the given time range.

## SELECT
This is much less important than in SQL. The default is `count()`, but we won't really have to use it much for basic queries. 

## Homework
1. What is the volume of jobs reviewed across all queues in JLM for February 2020?

```sql
FROM joblevelmoderation 2020-02-01 2020-03-01
WHERE
GROUP BY 
SELECT --defaults to count()
```

2. What are the 5 most common policy classifications in the India queue in January 2020?

```sql
FROM joblevelmoderation 2020-01-01 2020-02-01
WHERE job_country_code = 'IN'
GROUP BY answerclassifications[5]
SELECT --defaults to count()
```

3. What is the total volume of bad job decisions for the English queue in June 2020?

```sql
FROM joblevelmoderation 2020-06-01 2020-07-01
WHERE answer = 'badjob' queue = 'Job_Level_Moderation'
GROUP BY 
SELECT --defaults to count()
```

4. What is the name of the company that was reviewed the most in the English queue in the month of July 2020?

```sql
FROM joblevelmoderation 2020-06-01 2020-07-01
WHERE queue = 'Job_Level_Moderation'
GROUP BY companyname[1]
SELECT --defaults to count()
```

5. What company had the most ‘badjob’ reviews in the English queue in the month of June 2020?

```sql
FROM joblevelmoderation 2020-06-01 2020-07-01
WHERE queue = 'Job_Level_Moderation' answer = 'badjob'
GROUP BY companyname[1]
SELECT --defaults to count()
```

6. List the queues in order of volume of decisions made that were 'badjob' in July of 2021

```sql
FROM joblevelmoderation 2020-07-01 2020-08-01
WHERE answer = 'badjob'
GROUP BY queue
SELECT --defaults to count()
```

---
1. [Session page](https://wiki.indeed.com/display/JSOps/IQL+Training%3A+From+Beginner+to+Intermediate)
2. [Google doc worksheet](https://docs.google.com/document/d/1QbP4A4yuJv3gLm7A-FilTJfdP0ADSWo8RzySDitO-KA/edit#heading=h.8k60sbqz37nq)
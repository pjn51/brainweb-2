---
origin: 2022-07-05
aliases: []
---
# IQL - b2i session three
---
> [!info]
> This is part of [[IQL - From Beginner to Intermediate]].

In this session, we went over tokenization briefly, as well as how to group by time periods and graph our results. 

For the previous homework, there were a few minor corrections to my work, but nothing worth noting. The only thing to mention is that when we limit the results to the top or bottom $n$ results, that's going to rank them based on *volume* rather than whatever we're selecting for the query.

Moving on, [[tokenization]] was discussed - there are lots of [[IQL indices]] that tokenize string fields into their components. 

If we want to group by a time period, there are lots of ways to do so. 

Grouping by day: `GROUP BY time(1d)` or `GROUP BY time(1day)`
Grouping by week: `GROUP BY time(1w)` or `GROUP BY time(1week)`
Grouping by month: `GROUP BY time(1mo)` or `GROUP BY time(1month)`
Grouping by year: `GROUP BY time(1y)` or `GROUP BY time(1year)`

Note that all these shortcuts apply to the `FROM` clause as well. 

Furthermore, we should understand that when dealing with this kind of bucketing, we can run into partial segments. For instance, if we group by year, 2022 has not yet ended. By default, time periods that are not over will be excluded, but we can pass `GROUP BY time(1y ALLOW PARTIAL)` to keep the current year in our results, despite its incompleteness.

## Homework
1. What percent of jobs in JLM were marked badjob in March 2020?

```sql
FROM joblevelmoderation 2020-03-01 2020-04-01
WHERE 
GROUP BY 
SELECT answer = 'badjob' / count()
```

2. How many jobs were marked as Adult Industry for the English queue in July 2020?

```sql
FROM joblevelmoderation 2020-07-01 2020-08-01
WHERE queue = 'Job_Level_Moderation' 
GROUP BY
SELECT answerclassifications="GP_P_adultIndustry" / count()
```

3. What are the day to day changes in volume in the English queue for the month of June 2020?

```sql
FROM joblevelmoderation 2020-06-01 2020-07-01
WHERE queue = 'Job_Level_Moderation' 
GROUP BY time(1d)
SELECT 
```

4. For the English queue, what are the top 3 companies with the most badjob reviews in July 2021 where we’ve reviewed at least 50 jobs? (HINT: use the HAVING parameter)

```sql
FROM joblevelmoderation 2021-07-01 2021-08-01
WHERE queue = 'Job_Level_Moderation' 
GROUP BY companyname[3] HAVING count()>50
SELECT 
```

5. Of all of the origins across all of the queues in JLM, which origin has the highest bad job ratio in January of 2021?

```sql
FROM joblevelmoderation 2021-01-01 2021-02-01
WHERE 
GROUP BY origin
SELECT answer = 'badjob' / count()
```

---
1. [Video](https://indeed.zoom.us/rec/play/Q8WbKftUDtM85IdjcHZUl6xkz9nxjDMvjplH75RpFBiIVqxjOmEQmgs7svsfT6VRQ7_yMWGECZP2d2y0.8Ct89dRsBCv54mkv?continueMode=true)
2. [Worksheet](https://docs.google.com/document/d/1QbP4A4yuJv3gLm7A-FilTJfdP0ADSWo8RzySDitO-KA/edit#heading=h.8k60sbqz37nq)
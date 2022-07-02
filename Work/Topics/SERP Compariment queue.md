---
origin: 2022-06-22
aliases: 
---
# SERP Compariment queue
---
The SERP Compariment queue is a [[PM queues|PM queue]] that we can use to measure the performance of the [[SERP]] in relation to [[Indeed|Indeed's]] competitors. 

This queue was released in Q1 2022. 

---
```dataview
LIST 
FROM [[SERP Compariment queue]]
AND "Ideas"
AND -outgoing([[SERP Compariment queue]])
```


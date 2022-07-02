---
origin: 2022-06-21
aliases: 
---
# Job to Profile queue
---
The Job to Profile queue is one of the [[PM queues]] that [[Indeed]] uses to grade the performance of match providers within the [[recommended jobs platform]]. 

---
```dataview
LIST 
FROM [[Job to Profile queue]]
AND "Ideas"
AND -outgoing([[Job to Profile queue]])
```


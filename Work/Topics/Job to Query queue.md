---
origin: 2022-06-21
aliases: 
---
# Job to Query queue
---
The Job to Query queue is one of the common [[PM queues]] that [[Indeed]] uses. A moderator grades the performance of the job [[recommendation|recommender]] by comparing a query such as "Dental Hygenist" with a single job listing. 

This is relatively similar to the [[SERP Relevance queue]]. 




---
```dataview
LIST 
FROM [[Job to Query queue]]
AND "Ideas"
AND -outgoing([[Job to Query queue]])
```


---
origin: 2022-06-21
aliases: 
---
# SERP Relevance queue
---
The SERP Relevance queue is a [[PM queues|PM queue]] that [[Indeed]] uses to measure the performance of the [[SERP]] [[recommendation]] engine. 

A moderator rates the relevance of individual job listings, given a page of them that is the result of a query. 

The metric reported is called [[bad match rate]], which can be weighted or unweighted. Weighted BMR assigns a weight to queries based on popularity, such that a query with $x$ instances will have a weight of $x$. This metric is natually lower than unweighted BMR, since it's hard to recommend jobs for rare searches.

---
1. [Labeler queue](https://labeler.cmhprod1.k8s.indeed.tech/task/viewtask?taskName=US%20SERP%20Relevance)
```dataview
LIST 
FROM [[SERP Relevance queue]]
AND "Ideas"
AND -outgoing([[SERP Relevance queue]])
```


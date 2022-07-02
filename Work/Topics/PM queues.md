---
origin: 2022-06-21
aliases: [PM queue]
---
# PM queues
---
A product measurement queue is a [[Labeler]] task that the [[Product Quality Measurement]] team uses to measure the quality of [[Indeed]] tools and products. 

There are three central queues that I know of:

1. [[Job to Query queue]]
2. [[SERP Relevance queue]]
3. [[SERP Compariment queue]]

---
```dataview
LIST 
FROM [[PM queues]]
AND "Ideas"
AND -outgoing([[PM queues]])
```


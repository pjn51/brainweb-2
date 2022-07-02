---
origin: 2022-06-21
aliases: [SERPs]
---
# SERP
---
SERP stands for search engine results page. It utilizes a [[recommendation]] system powered by the [[recommended jobs platform|RJP]]. 

There are a few [[PM queues]] that grade SERP performance:

1. [[SERP Compariment queue]]
2. [[SERP Relevance queue]]


---
```dataview
LIST 
FROM [[SERP]]
AND "Ideas"
AND -outgoing([[SERP]])
```


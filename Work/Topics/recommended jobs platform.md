---
origin: 2022-06-21
aliases: [RJP]
---
# Recommended jobs platform
---
The recommended jobs platform, or RJP, is the central [[recommendation]] system that [[Indeed]] uses to feed job seekers new jobs in their feed or via email. 

Individual methods of recommendation are handled by the *match providers* [1] and then aggregated and ranked by the central RJP process

The performance of individual match providers is graded by the [[Job to Profile queue]]. 

---
1.  [Match providers wiki](https://wiki.indeed.com/pages/viewpage.action?pageId=423931180)


```dataview
LIST 
FROM [[recommended jobs platform]]
AND "Ideas"
AND -outgoing([[recommended jobs platform]])
```


---
origin: 2022-06-16
aliases: 
---
# Waldo
---
This is an [[internal Indeed tools|internal Indeed tool]] that the [[Job Seeker Operations|JS OPS]] team uses to review data on any job posting. 

Queries can find jobs with certain attributes, and "rules" can alter the [[visibility]] of those jobs. This is the way that [[Indeed uses visibility level as a moderation tool]]. 

---
```dataview
LIST 
FROM [[Waldo]]
AND "Ideas"
AND -outgoing([[Waldo]])
```


---
origin: 2022-06-27
aliases: []
---
# Alexandria
---
Alexandria is an [[internal Indeed tools|internal Indeed tool]] cataloging all the [[data]] that [[Indeed]] uses, including [[metadata]] about [[IQL indices]]. 

---
1. [Alexandria homepage](https://alexandria.sandbox.indeed.net/)
```dataview
LIST 
FROM [[Alexandria]]
AND "Ideas"
AND -outgoing([[Alexandria]])
```


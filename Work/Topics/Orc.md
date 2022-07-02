---
origin: 2022-06-28
aliases: []
---
# Orc
---
Orc is an [[internal Indeed tools|internal Indeed tool]] that schedules [[CRON job|CRON jobs]]. 

---
1. Briefly mentioned during [[22-06-28 IQL overview]]
```dataview
LIST 
FROM [[Orc]]
AND "Ideas"
AND -outgoing([[Orc]])
```


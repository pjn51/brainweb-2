---
origin: 2022-06-21
aliases: [Cron, Cronjobs]
---
# Cronjob
---
A Cronjob is a tool that automatically runs code. 

[[Indeed]] uses them to maintain [[PM queues]] by automatically moving data round. 

See this [spreadsheet](https://docs.google.com/spreadsheets/d/1o4GYZPpRneMzD3gVXI_eSBtK6v_HEpU4HTxNlE3WXu8/edit#gid=0) for a list of current Crons. 

---
```dataview
LIST 
FROM [[CRON job]]
AND "Ideas"
AND -outgoing([[CRON job]])
```


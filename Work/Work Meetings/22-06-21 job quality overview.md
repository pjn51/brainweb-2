# 22-06-21 job quality overview
on [[22-06-21 Tue]]
with Brian L

---
Brian and I went over a brief recap of the three most common [[PM queues]] that we work with. 

We discussed how the [[SERP Relevance queue]] used to sample tail queries, allowing insight into the more rare queries that [[Job to Query queue]] wasn't reaching, but that sampling method has changed to sample according to a [[normal distribution]] - now the J2Q queue actually does a better job with finding uncommon queries. 

Brian mentioned that [[bad match rate|BMR]] is the primary metric here, and that the 1000 most common queries have a significantly lower BMR than the less common ones. 

I asked how I would be interacting with these tools, and Brian said that I would perhaps be building [[CRON job|CRON jobs]], or actually creating new queues or maintaining existing ones. He said that Dylan would be a better source for that info. 

---
Here are the [notes](https://docs.google.com/document/d/1IlZNNo6M-8AO-876tN3GUDID9MYYJCqugSC5viqfbv4/edit) that Brian provided. Here is a [spreadsheet](https://docs.google.com/spreadsheets/d/1o4GYZPpRneMzD3gVXI_eSBtK6v_HEpU4HTxNlE3WXu8/edit#gid=0) of all the CRONs that the team is maintaining. 
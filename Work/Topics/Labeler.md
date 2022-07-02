---
origin: 2022-06-21
aliases: 
---
# Labeler
---
Labeler is an in-house [[Indeed]] tool for creating and managing workflows that are related to [[data annotation]] or moderation. It's an [[internal Indeed tools|internal Indeed tool]] managed by the Scaled Ops team. 

This is the tool that the [[Product Quality Measurement|PQM]] team builds [[PM queues]] with. 

Labeler is tightly linked with some [[IQL]] indexes so that we can query the annotated data produced by the queues. 

---
1. See my notes from [[22-06-21 intro to Labeler]]
2. I completed this [labeler exercise](https://docs.google.com/document/d/1PB0PNjpVD9thICm-lcmgYOIvpOClf3T4qGwcg89tiD8/edit) as part of onboarding
3. Here's the [wiki page](https://wiki.indeed.com/display/ScaledOps/Scaled+Ops+Labeler+Home)
```dataview
LIST 
FROM [[Labeler]]
AND "Ideas"
AND -outgoing([[Labeler]])
```


---
origin: 2022-06-16
aliases: [PQM]
---
# Measurement
---
This is a sub-team within [[Measurement & Tools]] in [[Indeed]]. I'm on this team as a Technical Analyst. 

## Standups
```dataview
LIST
FROM ("Work Meetings" OR "Personal/Work Meetings")
WHERE contains(file.name, "standup") AND contains(file.name, "PQM")
```
## Biweekly presentations
```dataview
LIST
FROM ("Work Meetings" OR "Personal/Work Meetings")
WHERE endswith(file.name, "biweekly")
```
## Sprint and biweekly planning
```dataview
LIST
FROM ("Work Meetings" OR "Personal/Work Meetings")
WHERE contains(file.name, "planning") AND contains(file.name, "PQM")
```

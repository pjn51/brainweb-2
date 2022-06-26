# Vault Refresher ♻
---
# Introduction
The purpose of this tool is to show me notes that I haven't modified in a long time. This could be a useful way to make sure that I'm refreshing my knowledge of all the topics of my vault, and expanding on what I've learned more about. I will filter out meetings, as I shouldn't really need to edit these after the fact. I've chosen to only show the ten files that are most stale.

```dataview
TABLE file.mday AS "Modified"
FROM ("Topics" OR "Literature & Reference" OR "People & Organizations" OR "Projects")
SORT file.mtime
LIMIT 10
```
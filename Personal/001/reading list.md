# Reading List


---
# Unread
See Todoist for a reading list. 

# In progress
```dataview
TABLE author, file.tags AS "tags"
FROM #wip
SORT file.name
WHERE file.name != "001 - start"
WHERE file.name != "lit template"
```

# Overall
I can use the following table to see which Literature & Reference notes haven't been edited in a long time. 

```dataview
TABLE file.mtime AS "Modified"
FROM "Literature & Reference"
SORT file.mtime
```
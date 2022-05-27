---
origin: {{date:YYYY-MM-DD}}
---
# 📅 {{date:dddd, MMMM DD, YYYY}}
`LINKS:` [[{{Yesterday}}|previous]] < [[{{date:YYYY-MM MMMM}}|month]] // [[journal]] > [[{{Tomorrow}}|next]] 
`TAGS:` #daily

---
# 💭 Thoughts and feelings


# 📝 Today's notes
```dataview
LIST 
FROM ""
WHERE file.ctime > this.file.day and file.ctime < (this.file.day + dur(1 day))
SORT file.ctime
```
# ✏️ Today's edits
```dataview
LIST
FROM ""
WHERE file.cday < this.file.day
WHERE file.mtime > this.file.day and file.mtime < (this.file.day + dur(1 day))
SORT file.mtime
```
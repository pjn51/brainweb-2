---
origin: 2022-06-27
aliases: [IQL index]
---
# IQL indices
---
[[IQL]] queries are really queries into indices. [[Indeed]] generates 60 billion log events daily and these events are automatically aggregated. ^1

These indices are cataloged within [[Alexandria]]. 

---
1. https://wiki.indeed.com/display/IQL/IQL+Index+Creation
2. See [Alexandria](https://alexandria.sandbox.indeed.net/) for a list of popular indices
```dataview
LIST 
FROM [[IQL indices]]
AND "Ideas"
AND -outgoing([[IQL indices]])
```


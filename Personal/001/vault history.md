# Vault History
---
# Stats
```tracker
searchType: fileMeta
searchTarget: cDate, numWords
xDataset: 0
folder: /
summary:
    template: "Total word count: {{sum(dataset(1))}}"
```

```tracker
searchType: fileMeta
searchTarget: cDate, numWords
xDataset: 0
folder: /Journal
summary:
    template: "Total journal wc: {{sum(dataset(1))}}"
```

# 2020 notes per month
```dataview
TABLE file.cday as "", length(rows) as "Notes"
WHERE file.cday.year = 2020
GROUP BY file.cday.month as "M"
```

# 2021 notes per month
```dataview
TABLE file.cday as "", length(rows) as "Notes"
WHERE file.cday.year = 2021
GROUP BY file.cday.month
```

# 2022 Notes / Month
```dataview
TABLE file.cday as "", length(rows) as "Notes"
WHERE file.cday.year = 2022
GROUP BY file.cday.month as "M"
```

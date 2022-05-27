---
origin: {{date:YYYY-MM-DD}}
---
# 📅 {{date: MMMM YYYY}}
`LINKS:` %%previous%% // %%next%% // [[{{year}}]]
`TAGS:` #daily 

---
# Stats
```tracke r
searchType: fileMeta
searchTarget: cDate, numWords
xDataset: 0
startDate:      // start of month
endDate:        // end of month
folder: /
summary:
    template: "Total word count: {{sum(dataset(1))}}"
```

```dataview
TABLE length(rows) AS total_notes
FROM -#daily
WHERE file.ctime.month = {{date: MM}} AND file.ctime.year = {{date: YYYY}}
GROUP BY true
```

> [!Summary]
> ...

> [!one] 
> ...

- Sunday:
- Monday:
- Tuesday:
- Wednesday:
- Thursday:
- Friday:
- Saturday:

> [!two] 
> ...

- Sunday:
- Monday:
- Tuesday:
- Wednesday:
- Thursday:
- Friday:
- Saturday:

> [!three] 
> ...

- Sunday:
- Monday:
- Tuesday:
- Wednesday:
- Thursday:
- Friday:
- Saturday:

> [!four] 
> ...

- Sunday:
- Monday:
- Tuesday:
- Wednesday:
- Thursday:
- Friday:
- Saturday:

---
# Notes from this month
```dataview
TABLE length(rows) AS Total Notes
FROM -#daily
WHERE file.ctime.month = {{month}} AND file.ctime.year = {{year}}
GROUP BY true
```
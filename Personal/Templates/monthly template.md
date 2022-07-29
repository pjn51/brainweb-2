---
origin: {{date:YYYY-MM-DD}}
---
# 📅 {{date: MMMM YYYY}}
`LINKS:` %%previous%% // %%next%% // [[{{year}}]]
#daily 

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

# Summary

# 1️⃣ First week

- Sunday:
- Monday:
- Tuesday:
- Wednesday:
- Thursday:
- Friday:
- Saturday:

# 2️⃣ Second week

- Sunday:
- Monday:
- Tuesday:
- Wednesday:
- Thursday:
- Friday:
- Saturday:

# 3️⃣ Third week

- Sunday:
- Monday:
- Tuesday:
- Wednesday:
- Thursday:
- Friday:
- Saturday:

# 4️⃣ Fourth week

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
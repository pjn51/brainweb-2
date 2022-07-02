---
origin: 2022-06-21
aliases: [BMR]
---
# Bad match rate
---
Bad match rate, or BMR, is a central [[metrics|metric]] that [[Indeed]] uses for measuring the performance of job [[recommendation]] tools.  

BMR is reported in a weighted and unweighted form. 

Weighted BMR dipped around April 2022 due to a sampling error being fixed. ^1

---
1. [Lynn's notes for my SERP metrics training](https://docs.google.com/document/d/1borIvtpOCDjNRAhkG78Q2GnfNkNxLEPMZrJJoMzqauo/edit#)
```dataview
LIST 
FROM [[bad match rate]]
AND "Ideas"
AND -outgoing([[bad match rate]])
```


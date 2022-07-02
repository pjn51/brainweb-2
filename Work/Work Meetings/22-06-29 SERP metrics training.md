# SERP metrics training
on [[22-06-29 Wed]]
with [[Lynn]], [[Josh]]

---
In this meeting led by Lynn, we discussed the various [[PM queues]] and the [[metrics]] that are associated with them. 
 
## SERP Relevance
In the [[SERP Relevance queue]], we're dealing with the only [[Data can be quantiative or qualitative|quantitative]] metric: [[bad match rate]]. I learned that BMR can be weighted or unweighted. When it's weighted, queries that are more popuar are given more weight, such that a query that has $n$ searches in the time period has a weight of $n$. This prioritizes having good matches for popular searches. Naturally, the unweighted BMR is higher, since it's hard to find good matches for uncommon searches.

## SERP Relrating
In the [[SERP Relrating queue]], vendors are taking user feedback from the [[SERP]] and categorizing it. Since categories aren't exclusive, it's more like tagging really. 

The categories and subcategories are lumped together by default in [[IQL]], but we can look only at either big-bucket or small-bucket if we want. We just have to group by a field that ends in `tok`, indicating that we're [[tokenization|tokenizing]] the categories field.

Lynn mentioned that self-reported relevance is a really debatable metric, since the person who now runs Invite 2 Apply used to work at Netflix, and said that they would sometimes get reports of a show being irrelevant, but the user would go on to watch it anyway!

## SERP Compariment
The [[SERP Compariment queue]] is still under construction, since it's hard to make sure the [[data]] are good and make sense to associate between sites. 

## Resources
Lynn made an excellent meetings notes doc with lots of resources. ^1
She also provided a list of useful IQL queries. ^2

---
1. [Notes for this meeting](https://docs.google.com/document/d/1borIvtpOCDjNRAhkG78Q2GnfNkNxLEPMZrJJoMzqauo/edit)
2. [Useful IQL queries](https://docs.google.com/document/d/1Ze9g60WJ-aATSOIt7sJ27MCfwB1ZdVxePgTpsljfn8w/edit)
---
origin: 2022-06-21
aliases: 
---
# Imhotep Query Language
---
IQL stands for Imhotep Query Language. As the name would imply, it's a [[SQL]]-like query language built around [[Imhotep]], [[internal Indeed tools|built by Indeed]].

The [[Labeler]] tool sends data into IQL indices. 

IQL is queried based on [[IQL indices]]. 

---
1. Here's the [IQL confluence home page](https://wiki.indeed.com/display/IQL/IQL+Home+-+Your+Primary+Source+for+All+Things+IQL)
2. You can find a list of Imhotep indices in [Alexandria](https://alexandria.sandbox.indeed.net/)
3. Here's the [IQL webapp](https://squall.indeed.com/iqlweb/#q[]=&author=pnorman&createTimestamp=1655935756&v=2&view=table) that we use to run queries in the browser
4. This is [[Lynn|Lynn's]] list of [useful IQL queries](https://docs.google.com/document/d/1Ze9g60WJ-aATSOIt7sJ27MCfwB1ZdVxePgTpsljfn8w/edit)
```dataview
LIST 
FROM [[IQL]]
AND "Ideas"
AND -outgoing([[IQL]])
```


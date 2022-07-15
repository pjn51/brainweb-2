---
aliases: 
---
# Dataview
---
Dataview is a community plugin for [[Obsidian]] that I use heavily within my vault. 

For a long time, I was using dataview to find hidden backlinks using the following code:

```
LIST
FROM [[this note]]
AND -outgoing([[this note]])
```

Dataview has syntax similar to [[SQL]], and it also allows [[JavaScript]] to query the dataview API. 

My [[thought cabinet]] is set up using the following dataviewjs code:

```
// assemble list of unique tags
let tags = []
for (let tag of dv.pages().file.tags) {
	if (tags.indexOf(tag) == -1) {
		if (tag.includes("idea")) { 
			tags.push(tag)
		} 
	} 

}

tags.sort();

// display unique tags as headers
for (let i = 1; i < (tags.length-1); i++) { // i = 1 to exclude "#idea" 
	dv.span;
	let tag = tags[i]
	dv.header(2, tag)
	dv.list(dv.pages(tag).file.link)
}
```

---
1. [Dataview functions documentation](https://blacksmithgu.github.io/obsidian-dataview/query/functions/)
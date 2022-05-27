# Question Index 🗃

---
# Introduction
This is the home of all my questions. I am experimenting with organizing my idea index in a question-based format, because we should [[Organize information for retrieval]] rather than just categorizing them into isolated buckets. 

# Unsorted
```dataview
LIST FROM #question 
WHERE contains(file.tags, "question/") = false
WHERE file.name != "question template"
SORT file.name
```
```dataviewjs
// assemble list of unique tags
let tags = []
for (let tag of dv.pages().file.tags) {
	if (tags.indexOf(tag) == -1) {
		if (tag.includes("question")) { 
			tags.push(tag)
		} 
	} 

}

// remove a few tags that I don't want
var index = tags.indexOf('#idea')
if (index > -1) {
	tags.splice(index, 1);
}

var index = tags.indexOf('#question')
if (index > -1) {
	tags.splice(index, 1);
}

tags.sort();

// display unique tags as headers
for (let i = 0; i < (tags.length); i++) {
	dv.span;
	let tag = tags[i]

	// count terms to determine tag level ("ideas/politics" has 2 terms)
	let terms = (tag.split('/'))

	// add breaks between main sections
	// if (terms.length == 2) {
	//	dv.paragraph('$$* \ * \ * \ * \ * $$')
	// }

	// print only relative section (for "#idea/stem/math" print "math")
	let lastItem = terms[terms.length - 1]

	// uppercase the header
	let firstChar = lastItem[0].toUpperCase()
	let otherChars = lastItem.substring(1)

	dv.header(3, firstChar+otherChars)

	dv.list(dv.pages(tag)
	.sort(p => p.file.name, 'asc')
	.file.link)
}
```

# Floating ideas
%%I want to have a list of idea notes that aren't connected to any question, and don't even have links that connect them to any questions. Not sure how to do this yet. See my [[floating idea finder project]]%%


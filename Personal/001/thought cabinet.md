# Thought Cabinet 🗃
#hub 

---
This is the index of all my idea notes. I prefer flexible and associative tagging to strict categorization ([[Emergent associations beat predetermined categorization]]). There are several principles by which I develop idea notes, which can be found in my [[style guide]] page and in my [[thought cabinet workflow]]. Questions appear at the top, and act as organizing structures for ideas. 

A very important question for this page: [[How should my index be organized?]] Currently, [[dataview]] provides the backbone of this organization. 

---
```dataviewjs
// assemble list of unique tags
let tags = []
for (let tag of dv.pages().file.tags) {
	if (tags.indexOf(tag) == -1) {
		if (tag.includes("idea")) { 
			tags.push(tag)
		} 
	} 

}

// remove a few tags that I don't want
var index = tags.indexOf('#idea')
if (index > -1) {
	tags.splice(index, 1);
}

var index = tags.indexOf('#idea/_')
if (index > -1) {
	tags.splice(index, 1);
}

var index = tags.indexOf('#idea/question')
if (index > -1) {
	tags.splice(index, 1);
}

tags.sort();

//put questions and inbox at the top
dv.header(3, "Inbox")
dv.list(dv.pages("#idea/_")
	.sort(p => p.file.name, 'asc')
	.where(p => p.file.name !== 'idea template')
	.file.link)

// display unique tags as headers
for (let i = 0; i < (tags.length); i++) {
	dv.span;
	let tag = tags[i]

	// count terms to determine tag level ("ideas/politics" has 2 terms)
	let terms = (tag.split('/'))

	// add breaks between main sections
	if (terms.length == 2) {
		dv.paragraph('$$* \ * \ * \ * \ * $$')
	}

	// print only relative section (for "#idea/stem/math" print "math")
	let lastItem = terms[terms.length - 1]

	// uppercase the header
	let firstChar = lastItem[0].toUpperCase()
	let otherChars = lastItem.substring(1)

	dv.header(terms.length+2, firstChar+otherChars)

	dv.list(dv.pages(tag)
	.sort(p => p.file.name, 'asc')
	.file.link)
}
```

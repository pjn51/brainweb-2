# Floating Idea Finder

---
## 2022-01-13
The idea for this project is to figure out a way to find all the idea notes that are not connected to a question note on any level (first-level, second-level, etc).

Here's my general idea of how this should work:

```
// create list of all notes linking to specific note
	// pass specific note to function
	// get list of all first-level links
		// check for NEW notes
		// if NEW notes in list
			// pass each note to the function
			// get THEIR links
			// check for NEW notes
			// etc...

// check for connection to a question note
	// see if "?" in the list
// return all notes without such a connection
```

First, lets just try to get a working list of all first-level connections to a given note. 

```dataviewj_s
function linkFinder(note) {
	return dv.list(dv.page(note).file.link)
}

dv.paragraph((linkFinder(dv.current().file)))
```
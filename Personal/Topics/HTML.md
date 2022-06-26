# HTML
`TAGS:`

---
# Introduction
HTML is the language that websites are written in. I don't really need to know much about HTML for the purposes of [[data science]], other than how to find things on a page of HTML during [[web scraping]].

Everything in HTML is contained in tags, such as `<head></head>` or `<body></body>`. These are often nested to hell, and I can use these tags to find what I want to scrape off a web page.

In order to apply formatting, elements on a website have identifying information about them. This could be their class, or their id. Classes can contain multiple elements. For example, all the body text in a news article might have the class 'article-text'. But each element must have a different ID. That has to be unique. 

A basic webpage might look like this...

```html
<html>
	<head>
		<title>Website Title!</title>
	</head>
	<body>
		<h1>Website Heading</h1>
		<p class='main-text'>blah blah blah blah blah</p>
	</body>
</html>
```

# Using HTML in Obsidian
I can actually take advantage of HTML rendering in [[Obsidian]]. 

<center>
	Text can be centered, but markdown doesn't work using HTML notation. 
</center>
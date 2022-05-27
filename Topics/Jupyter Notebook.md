# Jupyter Notebook
`TAGS:`

---
We use Jupyter Notebook, which is an Integrated Development Environment. This is what we will be using for the whole bootcamp. 

We can format text, write whole paragraphs, and of course execute code all inside a Notebook. 

Jupyter Notebook is quite useful for our purposes. We can test individual lines of code. 

There are ‘code’ cells and ‘markdown’ cells. Markdown cells are used for putting in other kinds of text or explanations beside the actual Python code. They are compatible with mathematical expressions using LaTeX. 

When we enter a cell, we engage ‘edit mode.’ We can use ‘command mode’ to change the document as a whole without changing any individual cell.

Magic commands are provided by Jupyter 
	`%env` gets a list of variables
	`%timeit` allows time execution of a kernel (how long it took to execute)
	`%pwd` tells you your working directory

## Note Taking in Notebooks
Jupyter Notebook is also excellent for taking [[Python]] notes. Since I can write working code blocks and use markdown cells to note what I'm doing, it is a very fast way to track my thinking in regards to code. 

## My Extensions
Currently, I have the `nbextensions` plugin, which makes working with most extensions a breeze. However, there are some that aren't in there that I need to keep track of to some extent. 

I'm using `jupyter-themes` which is run via the [[command line]].
```
jt -t onedork 					# change the theme to onedork

jt -t onedork -fs 13 -ofs 13 	# change the theme to onedork, set code font size to 13 and output 
								# font size to 13
```
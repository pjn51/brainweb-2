# Metis Notes for Friday, Feb 5th
`LINKS:` [[metis week 5]]
#meeting/career

---
We're starting off with pair programming like usual, and then we have lectures on plotly / dash, and another classification assessment. 

## Lecture - [[plotly]]
- Check out the `ONL_DS5-plotly.ipynb` notebook. 
- Plotly is a library in python. 
- Importing
	- Standard practice is to `import plotly.figure_factory as ff` and `import plotly.graph_objs as go`
	- We should also pass `from plotly.offline import download_plotlyjs, init_notebook_mode, plot, iplot`
- Plotly express
	- `import plotly.express as px`
- Benefits of plotly
	- Lots of 'cool' stuff. 
	- Interactivity, 3D graphs, and sliders and stuff. 
	- Great with maps. We can animate them by year pretty easily. 

## Lecture - [[dash]]
- This is built on plotly, and functions as a way to move [[data]] visualization onto the internet. 
- It basically allows us to create an app that will display a plotly visualization hosted on our local server. 
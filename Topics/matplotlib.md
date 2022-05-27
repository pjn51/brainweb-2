# Matplotlib
`LINKS:` [[data visualization]]
`TAGS:`

---
This python [[modules and packages|package]] is centered around [[data visualization]]. 

## Creating charts
We can create a line chart from any data type.

```python
plt.plot(my_data)
```

This will create a line plot of the data found in `my_list`. 

If we provide just one argument (`my_data` above), then matplotlib will assume those  values are the y axis values of the chart, and assumes the x-axis values are the indices of the list.

If we want to manually set the x-axis, we can pass in multiple variables, with the first one standing for the x axis, and the second one for the y.

## Customizing chart elements
If we want to change the title of a chart, pass... after you’ve created a plot. 

```python
My_plot = plt.plot(my_data)

my_plot.title(“insert title here”)
```

There are many ways to customize titles, from changing font type, style, font size, rotation, and other things by using optional parameters for the `.title( )` method. 
We can add x and y labels as well, using the `.xlabel( )` and `.ylabel( )` methods. 
If we want to have multiple lines in one plot, simply execute `plt.plot( )` multiple times within one cell. 

For more customization, check out all the stuff in the docstring and you can see how complex we can change the look of these charts.

## Chart types
Matplotlib can create...
- line charts: `plt.plot( )`
- bar charts (with or without error bars): `plt.bar( )`
- scatter plots: `plt.scatter( )`
- Histograms: `plt.hist( )`
- pie charts: `plt.pie( )`

## Advanced formatting
We can change figure size by passing `plt.figure(figsize=[width,height]`

We can change to scale to a log scale by applying the `np.log( )` function to the y data inside the `plt.plot( )` function. This is using [[NumPy]].

`plt.plot(my_x_data, np.log(my_y_data))`

An alternative to this method would be to instead use the function `plt.semilogy( )` to display your plot. This function will display the result in a log scale. 

## Subplots
We can create multiple plots in one result. 

`plt.subplot(# rows, # columns, # number of plot)`

“# of plot” specifies which plot we are currently modifying. So we would pass this first line and then create the first plot, then pass the line again but with 2 instead of 1 in the third parameter, and so on. 

In order to save images, we pass `plt.savefig(‘filename.png’)`

We can even make plots look like xkcd by using `plt.xkcd( )`. 

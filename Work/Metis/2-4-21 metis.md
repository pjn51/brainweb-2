# Metis Notes for Thursday, Feb 4th
`LINKS:` [[metis week 5]]
#meeting/career

---
## Pair programming
Given enough pennies (1 cent) and nickels (5 cents), how many ways can you make change for a given number of cents? Your function will be def ways(cents).

```python
def ways(cents):
    num_ways = 1
    for i in range(cents // 5):
        num_ways += 1
        
    return num_ways
```

Here's a better way:
```python
def ways(cents):
	return cents // 5 + 1
```

Given enough two-cents (a mythical coin) and nickels (5 cents), how many ways can you make change for a given number of cents? Your function will be def ways(cents).

```python
def ways2(cents):
	num = 0
	num_ways = 0
	
	if cents % 2 == 0:
		num_ways += 1 # solution w no nickels
		
	for num_fives in range((cents//5)+1):
		remainder = cents-5*num_fives
		if remainder % 2 == 0:
			num_ways += 1
			
	return num_ways
```

What about dimes, nickels, and 2-cent pieces? We can use the previous function
```python
def ways3(cents):
	num_ways = 0
	
	for tens in range((cents//10)+1):
		rem = cents - 10*tens
		ways += ways2(rem)
```

Recursive way:
```python
def ways_rec(cents, coinss):
	if len(coins) == 1:
		if cents%coins[0] == 0:
			return 1
		else:
			return 0
		
	ways = 0
	for count in range((cents//coins[0])+1):
		rem = cents-coins[0]*count
		ways += ways_rec(rem)
```

[[recursion]] is a fundamental CS concept, so we should be able to recognize when to use it. It looks great in interviews. 

## Lecture - [[data visualization]]
- Agenda
	- Why visualize
	- Popular tools
	- Best practices
	- Create tableau dashboard
- Why is [[data]] viz needed?
	- We do data viz in order to perform EDA, to tell a story, and to evoke emotion. 
	- At the end of the day, your audience will remember the narriative and the way you made them feel. 
- Data visualization workflow
	- Don't start with a chart.
	- Start with a takeaway or emotion in mind
	- Get feedback and iterate on the method of visualization
- Buzzfeed case study
	- Buzzfeed organizes their content by emotion!
	- Every article is categorized by how the content should make the user *feel*, no matter what it is actually about. 
- Emotions to emphasize
	- ==Surprise== is a common one. 
	- We are often surprised by our findings, and we can pass this emotion on. 
	- ==Calmness== is another one.
	- This helps prepare the audience for more complex findings. 
	- ==Interest== can be evoked through more interesting visualizations than just bar charts.
- Have the ==title== be an *insight* instead of just a description of what is being plotted. 
- Remember that the goal is not necessarily to portray the data accurately, but to serve a need. The metro map is not perfectly accurate, but it serves its purpose well. 
- There are lots of different tools for data visualization. We can use tools that we've seen before, like [[matplotlib]] or [[Excel]], but we can also use new tools like [[Tableau]]. 
### Best practices in data visualization
- Agenda
	- What to do
	- What not to do
	- How to do a makeover
- Basic charts
	- ==Big numbers==: this counts as a viz! Make the number bigger if it's meant to be a *big* number. 
	- ==Tables==: this works under the right circumstance, like comparing across categories. Don't over-use them or have them be too many rows or columns. 
	- ==Bar chart==: good for comparing groups / categories. Can be used for change over time. Sort them based on something meaningful. Start scales at zero! 
	- ==Histograms==: represents distribution of the data. The range of values must be binned. Can be normalized in terms of y. 
	- ==Line charts==: Good for change over time or forecasting. Only use them for continuous data. 
	- ==Scatter plot==: Good for continuous data on both axes. 
	- ==Bubble chart==: Like a scatter plot, with additional variable determining bubble size. You could use color change instead of size, since size difference is hard to gauge quickly. 
	- ==Pie chart==: not great for most situations. Best for categorical data. Order the segments meaningfully. Hard to read when there are more than like 3 segments. 
	- ==Heat map==: use these when you'r emplasizing a trend or pattern. 
- Bad visualizations
	- They tend to have too much going on, or superfluous information that isn't related to the message of the plot. 
	- The "Norman Door" is one which doesn't tell the user to push or to pull based on the look of the door. These doors often have to have a little sign on them. 
- ==Discoverability==: The ability to discorver what operations one can do / what the information in front of you means.
	- Charts should have this quality.
- Text
	- Orient all text horizontally. 
	- Make the font size readable! 
- Color
	- Max 5 colors. 
	- Use color palettes that go together. There are sites where you can find good palettes. 
	- Based on if the data is sequential, categorical, or diverging, choose a dataset that makes the most sense. 
	- Make sure the colors are still distinct when using greyscale, or for those who are colorblind. 8% of the male population is colorblind! 
		- Use blue and orange instead of red and green. 
- Highlight
	- Highlighting the essential information allows people to get the message a lot faster. 
- Background and foreground
	- Balance these two in terms of color and intensity
	- Conclusion should be in the foreground, non-essential info goes to the background
- The data-ink ratio
	- "Above all else, show the data" - Tufte
	- Nearly everything in the chart should be about the data. Very little ink should be wasted on non-essential information
- 30 sec rule
	- If your viz can't be understood in 30 seconds, rework it. 
- Common mistakes
	- Using 3d when it makes the data harder to understand
	- Using pie charts that have similarly-sized slices
	- Not starting the scale at zero to over-emphasize differences. 

## Lecture - [[Tableau]]
- [[Tableau]] is really a business intelligence and analytics tool
- It allows for interactivity and cool dashboards containing multiple methods of visualizing the data. 
- *I had issues with downloading it because it doesn't support the M1 chip. This made me fall behind a bit in the lecture.*
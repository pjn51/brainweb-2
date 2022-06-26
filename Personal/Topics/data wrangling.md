# Step 2: Data Wrangling
`LINKS:` [[data science workflow]]

---
Tip: always read the metadata for your source. 
# Methods of collecting data
We can either download CSVs, or we can use [[web scraping]] to get data from websites that don't want to let us download their data directly. 

# Why clean our data?
Data comes into our view with a lot of mess. There are duplicates, unnecessary data, typos, missing chunks, and outliers, just to name a few. 

## Typos
The first thing we should do is check the [[summary stats]] for all the data. Do the min and max values make sense? What are the unique values? These can be hints towards finding errors or outliers in the data. 

## Duplicates
Look at duplicates and think about why they are there, and if they should be there. Filter down the data to a reasonable degree. 

## Missing data
For missing data, we have some options. We can remove all rows with missing data, or we can impute some value into the empty cells. This value could be the most common value, the mean, etc. Think carefully about what makes the most sense for the situation. 

## Outliers
For outliers, we want to verify that they aren't inaccurate representations of the data. Some data truly does have outliers, but a lot of the time outliers are errors in one way or another. 

The best ways to find outliers are to use plots, [[statistics]], and [[residuals]]. 

A plot such as a histogram or box plot can show distinct outliers visually. These outliers can be quantified using statistical measures. 

# Normalization
[[When should we normalize our data?]]
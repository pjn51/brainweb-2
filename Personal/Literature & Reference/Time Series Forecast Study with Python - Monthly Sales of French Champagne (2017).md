---
author: Jason Brownlee
rating: 
genre: tech
format: article
---

# Time Series Forecast Study with Python - Montlhy Sales of French Champagne
`LINKS:` [source](https://machinelearningmastery.com/time-series-forecast-study-python-monthly-sales-french-champagne/)
`TAGS:` #article #wip 
`AUTHOR:` Jason Brownlee

---
## Overview
The author says that we will work through the following steps:

1. Environment
2. Problem description
3. Test harness
4. Persistence
5. Data analysis
6. ARIMA models
7. [[model validation]]

## 1. Environment
Brownlee says that we will use SciPy, [[NumPy]], [[matplotlib]], [[Pandas]], [[Scikit-Learn]], and statsmodels. 

## 2. Problem description
The author introduces the dataset, saying that the goal is to predict the number of monthly sales of chamapagne between 1964 and 1972. He outlines that there are 105 observations here. 

## 3. Test harness
Brownlee says we must develop a "test harness" to investigate the data and evaluate candidate models. He explains that this involves two steps: defining a testing dataset, and developing a method for model evaluation. 

## 3.1 Test dataset
Brownlee advises us to pretend that the year is 1971 and withold the last year of data from analysis and use it to test the final model. He uses the following code to load the data into Pandas, and split it into two segments (for some reason, he does this manually instead of using `train_test_split()`, and then for some reason he makes these dataframes back into CSVs... ).

```python
import pandas as pd
series = pd.read_csv('champagne.csv')
split_point = len(series) - 12
training, testing = series[0:split_point], series[split_point:]
training.to_csv('training.csv')
testing.to_csv('testing.csv')
```

## 3.2 Model evaluation
The author says that model evaluation can be broken into two elements: performance measure and test strategy. 

## 3.2.1 Performance measure
The author decides to use [[RMSE]] as the [[metrics|metric]] for model evaluation. He says this is because it gives more weight to predictions that are grossly wrong and will have the same units as the original data. 

He notes that any transformations to the [[data]] must be reversed before we calculate RMSE so that we can compare between different models. He also says that we can easily find RMSE by taking the square root of the scikit-learn function `mean_squared_error()`. 

## 3.2.2 Test strategy
Brownlee recommends using "walk-forward validation." By this, he means we should take the first 50% of the data as testing, and the remaining 50% as validation. For each step in the test dataset, the author argues, we should train a model and make a one-step prediction that is stored for later evaluation. Then, he says, we should take the actual observation from the test dataset and add it to the training dataset for the next iteration. 

Given the small size of the data, the author decides to allow the model to be re-trained on each new iteration. He uses the following code to split the training data, and iterate over the time steps in the validation dataset, adding a new observation each iteration. I think that the `yhat = ...` just indicates that he hasn't written that segment of code yet.

```python
# split train and val
X = series.values
train_size = int(len(X) * 0.5)
train, val = X[0:train_size], X[train_size:]

# walk-forward validation
history = [X for x in train]
predictions = list()

for i in range(len(test)):
	# predict
	yhat = ...
	predictions.append(yhat)
	
	# observation
	obs = test[i]
	history.append(obs)
	print('>Predicted=%.3f, Actual=%3.f' % (yhat, obs))
```

## 4. Persistence
Brownlee argues that we should establish a performance baseline before starting analysis. He says we should do this because it creates a benchmark that we can compare future models to.

He says that for forecasting, we call this benchmark the *persistence.* According to him, we take the previous step as the prediction for the next step. In the following code, he plugs this naive baseline into the test harness that he created above. I've taken the liberty of turning this test harness into a function, which Brownlee did not do. I set the default value of the `method` argument to be `history[-1]`, meaning that we predict the next value to be the previous value.

```python
def test_harness(method=history[-1])
	X = series.values
	train_size = int(len(X) * 0.5)
	train, val = X[0:train_size], X[train_size:]

	# walk-forward validation
	history = [X for x in train]
	predictions = list()

	for i in range(len(test)):
		# predict
		yhat = method
		predictions.append(yhat)

		# observation
		obs = test[i]
		history.append(obs)
		print('>Predicted=%.3f, Actual=%3.f' % (yhat, obs))
	
	mse = sklearn.mean_squred_error(val, predictions)
	rmse = sqrt(mse)
	print(f'RMSE: {rmse}')
```

The author says that when we run this naive baseline method, we see that we have a RMSE of 3186. He says that this means the average model prediction was off by 3,186 units, or in this dataset, 3,186 million sales.

## 5. Data analysis
The author insists that we should look at the data from five perspectives: 

1. [[summary stats]]
2. Line plot
3. Seasonal line plots
4. Density plots
5. Box and whisker plot

## 5.1 Summary statistics
The author uses `series.describe()` to calculate and print summary statistics for the time series.

## 5.2 Line plot
The author uses the Pandas plotting functionality to create a line plot showing sales over time. He says that this demonstrates that there is an increasing trend of sales over time, and systematic seasonality. 

<img src='https://machinelearningmastery.com/wp-content/uploads/2017/01/Champagne-Sales-Line-Plot.png'>

Importantly, the author notes that this time series is non-stationary.

## 5.3 Seasonal line plots
Seeking to confirm that there is seasonality in the data, the author creates a plot for each year of the [[data]] and compares them with each other using the following code.

```python
import pandas as pd
import matplotlib.pyplot as plt

groups = series['1964':'1970'].groupby(pd.Grouper(freq='A'))
years = pd.DataFrame()
plt.figure()
i = 1
n_groups = len(groups)

for name, group in groups:
	plt.subplot((n_groups*100) + 10 + i)
	i += 1
	plt.plot(group)
	
plt.show()
```

When the author executes this command, he recieves the following plot. 

<img src=https://machinelearningmastery.com/wp-content/uploads/2017/01/Seasonal-Per-Year-Line-Plots.png>

Based on this image, the author concludes that there is a dip each August and a rise from August to December in each year. 

## 5.4. Density plot
The author says that seeing the density of observations will give us further insight. He uses the following code to create a historgram and density plot of the observations without any temporal structure.


---
aliases: 
---
# Project overviews
---
> [!Info] 
> This is an overview page for all my [[Metis]] and work-related projects. Each project ought to have a broad description, as well as a list of tools and techniques used in the project. Descriptions ought to follow the [[STAR method]]. 

# 2. [[natural amenity regression]] // [repo](https://github.com/pjn51/beauty-and-value) // [slides](https://docs.google.com/presentation/d/1Jy7rKd2SJnnytMXXj4LNdostWFSXx9fIg5YJZOA-9x0/edit#slide=id.gb7c17aee2b_0_120)
My goal was to create a regression model that could incorporate information about the natural beauty of an area into traditional models of housing price. I gathered data from lots of different sources, stitched them together and cleaned them up, and then ran a series of models to see which would give the best performance. My final model was a regularized ridge regression that wasn't perfect, but did demonstrate that scenic beauty does have a price impact. I presented this information, with explanatory charts, to my classmates. 
## Tools and methods
- [[Pandas]] for data stitching, cleaning
- [[Scikit-Learn]] for train-test split and cross validation
- [[Scikit-Learn]] for their implementation of [[LASSO regression]] and [[ridge regression]] at various [[regularization]] intensities
- Evaluation using $\text{R}^2$ metric
- [[matplotlib]] for data visualization
- Presentation to stakeholders

# 3. [[fake job classifier]] // [repo](https://github.com/pjn51/detecting-fake-jobs) // [slides](https://docs.google.com/presentation/d/1KvXHXcoVy2SEIdUdetwpxgQSy8AivyhGdmphz1GvHG8/edit#slide=id.gbbf0cf8528_0_60)
My goal was to create a classifier that could aid a job board or job seekers in determining the trustworthiness of a job listing. I was able to leverage the text of the job listing to get a pretty good idea of the trustworthiness. 
## Tools used
- Pandas for data cleaning and exploratory analysis
- Class balancing through oversampling
- Train-test split using sklearn functions
- Feature extraction via count vectorizer from sklearn
- Evaluation using ROC curve (precision and recall at various thresholds)
- Final model was [[logistic regression]] with 0.78 recall, 0.8 precision on test set. 

# 4. [[covid tweet investigation]] // [repo](https://github.com/pjn51/covid-topic-modeling) // [slides](https://docs.google.com/presentation/d/12tiRfYU8afuOhseVB7rhtYnXBJq5vBSzWY8IJQyvZ3Q/edit#slide=id.gc07639392a_0_88)
I wanted to investigate the conversation on Twitter about the pandemic, and see if sentiment related to the intensity of [[COVID-19]] across the country. In order to do this, I pulled over half a million tweets using the Twint library, extracted text features, performed [[sentiment analysis]], and linear regression to see if there was a relationship. There was not, but I learned valuable information about how to gather information from Twitter and practiced presenting technical information. 
## Tools used
- [[NLP]]
- TextBlob to analyze polarity (emotional intensity) and subjectivity (-1 to 1)
- Topic modeling using non-negative matrix factorization ([[NMF]])
- [[linear regression]] of sentiment, topic, vs COVID case density
- Presented my results in terms of business use case

# 5. [[wildfire classifier]] // [repo](https://github.com/pjn51/modeling-wildfire-risk) // [slides]()
I wanted to create a tool that would allow firefighters and planners to intelligently distribute resources to the most at-risk counties. I decided to create a regression model to predict the amount of burnt space per county, but found that there was too much variance to be a useful tool. I responded by changing to a classification tool, where the user could specify a variable threshold that would update the model. I deployed the tool to a web app so that users could play around with the model. 
## Tools used
- Stitching, cleaning heterogenous data with Pandas
- Followed MVP, iterative protocol
- Modeling using multiple classification and regression algorithms, from linear regression up to Extra Trees classification
- Adapted to poor regression results by incorporating multi-threshold classification 
- Deployment via streamlit
- Variable thresholds handeled with dynamic class balancing using oversampling / undersampling based on data availability
- Presented my results in terms of business impact

# 6. [[stash-o-matic project]]
I was brought on to create a predictive model that could help automate the purchasing of inventory. However, I found the data weren't consistent enough for this task, so I decided to pivot towards creating more consistent data ingestion pipelines to build better data going forward, and created a series of internal tools and dashboards that relied in part on workers' understanding to educate the model. These tools have been very useful in enhancing estimation of inventory needs. 
- S: brought on to help with inventory management and prevent sellouts
- T: wanted to create predictive model of inventory needs, optimal resupply strategy based on very inconsistent data
- A: created robust data ingestion systems, cleaned lots of data, created dashboards and internal tools to aid in estimation
- R: lots of value from that tool already, created possibility of prediction in future, learned a lot about how to translate managment needs to analytical tasks
## Tools used
- [[Git]] for version control 
- Data management via [[MongoDB]], [[MySQL]], [[Excel]]. 
- ETL pipeline creation from multiple data sources into [[MongoDB]] using a standard schema to enable [[Python]] analysis.
- Made presentations using [[matplotlib]], [[seaborn]], and [[tableau]], as well as a proprietary dashboard tool that preceded my involvement. 
- Well-rounded role, involving the domains of data engineering, data science, and even backend development. 
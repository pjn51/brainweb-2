# Natural Amenity Regression
---
I was tasked with creating a [[regression]] [[modeling|model]] that could predict some numeric target for my first independent project of the [[Metis]] bootcamp. 

I decided to attempt to model median house price on the county level, using a dataset of [natural amenity scores](http://www.ers.usda.gov/data-products/natural-amenities-scale.aspx  ) as well as some population density and urbanization metrics that I scraped from Wikipedia (These natural amenity metrics were average winter and summer temperatures, winter sunlight hours, humidity, and an overall "score" that the USDA developed). 

However, I soon ran into a problem. There was very little variance in median home prices at the county level, so I decided to change my target to median price of houses at the level of metropolitan statistical areas, or MSAs. I imported new data, and associated the county-based data to the MSAs. This introduced some new assumptions, but I was comfortable with that. 

I performed a test-[[model validation|validate]]-train split on my [[data]], standard-scaled my variables, and performed [[LASSO regression|LASSO]] and [[ridge regression|ridge]] regression using cross validation to determine alpha intensity. I compared results for using environmental features only with a model trained on all features. I dropped some outliers, three Californian cities that seemed to be unpredictable by my model, and added an exponential feature. 

The final result for this process was a ridge regression that was trained on a combination of natural and human features, that explained 52% of the variance in median home prices. While this isn't great by itself, it demonstrates that the natural beauty of an area does have a measureable impact on the housing market. 

See my [slides](https://docs.google.com/presentation/d/1Jy7rKd2SJnnytMXXj4LNdostWFSXx9fIg5YJZOA-9x0/edit#slide=id.gb7c17aee2b_0_120) and my [repo](https://github.com/pjn51/beauty-and-value). Also see some [metadata](https://docs.google.com/document/d/1Qa4Du8fr3zx_udXFH5gFFdovKwKH81LuYWngdEAwpNg/edit) for the natural amenity dataset. 
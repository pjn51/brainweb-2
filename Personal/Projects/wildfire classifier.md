# Metis Project Five: Anticipating Wildfires Using Machine Learning

---
The fifth and final project as part of the [[Metis]] course. This is meant to be our passion project. 

For an overview of the project requirements, see my [[3-1-21 metis]] notes.

For Brian's input on the project, see my [[3-3-21 metis]] notes. 

## Interview with Purander
- There are never enough resources for each fire.
- Severity: they will pre-position resources based on drought and heat waves. 
- NWCG: national wildfire cooperating group.
- NIFC: National interagency fire center does lots of modeling and prediction. They issue situation reports that could be useful, as well as lots of maps.
- ==Anchorpoint== is a company that does software (noharm) that looks at sub-county wildfire prediction. The chance of wildfire, and the chance that the fire will be severe. This has lots to do with topography since south facing slopes tend to be drier and hotter. They have a proprietary algorithm. 
- ==Redzone== is a company that does a similar thing. 
- Check out *situation reports* issued by the National Interagency Coordination Center. 
- Fuels, weather, and topography influence fire patterns. 
- Resources that are moved around
	- Slurry bombers
	- Hand crews to dig ditches
	- Trucks / fire engines
	- Teams to 'treat' houses in neighborhoods in the fire's path (remove fuels, drench houses with water, etc)
	- Bulldozers to dig ditches
	- Bucket helicopters

## Workflow Overview
This is a really complex data flow, so I want to map out all the data that I'm messing around with.

1. Import all 1.88 million wildfire records using [[SQL]] as `all_fires`.  
2. Format `all_fires`
	1. Rename some columns
	2. Create STATE_CODE, 


Changing workflow!! It seems easier to start with counties and then add fires.

1. Create DataFrame of all counties, `fips`
2. Duplicate counties so that each year is represented as its own obervation, compile into new dataframe `fips_yrs`
3. Create FIPS_YEAR column in `fips_yrs`
4. Import fire data and format it
	1. Create FIPS_YEAR column
5. Add fire data to `fips_yrs`
6. Fill in NaNs in the FIRE_SIZE column with zeros.

## Final todo
- [x] Replace scary fire photos with happy forest
- [x] Create introduction slide
- [x] Cut my criticism / next steps to save on time
- [x] Unify theme (either dark or light)
- [x] Animate stuff
- [x] Reach out to Purander to ask what his formal position is for the shout-out
- [x] Finalize script
- [x] Record video!

# Blog

## Situation
Staring out the window of my middle school science classroom, it seemed like Hell itself had arrived on the outskirts of Boulder, Colorado. The smoke practically covered the sun, and the lesson plan was disrupted by the sounds of helicopters and low-flying planes buzzing back and forth to deliver water and flame retardant to the Fourmile Canyon fire. That fire would go on to burn 6,181 acres, destroy 168 homes, and cost an estimated $217 million in property damages [^1]. 

[^1]: https://en.wikipedia.org/wiki/Fourmile_Canyon#2010_wildfire

Unfortunately, that fire is far from an anomaly these days. In 2020, the wildfires in the western United States cost up to $13 billion in property damages, not to mention the lives lost and the heartache of countless families forced to rebuild [^2]. 

[^2]: https://www.reuters.com/article/us-usa-wildfires-insured-losses-trfn/western-u-s-wildfires-cost-insurers-up-to-13-billion-in-2020-idUSKBN28P2NQ

Wildfires aren't an unstoppable force - it was the efforts of humanity that were able to put a stop to the Fourmile Canyon fire, and to many other fires that have threatened our communities. One of the most important tools for fighting fires is understanding where the most high-risk areas are, so that we can pre-deploy firefighting resources to arrive as soon as possible. 

I was inspired to create a classification tool that could help humanity better stage firefighting resources after my time in the [[data science]] bootcamp offered by Metis](https://www.thisismetis.com/bootcamps/online-data-science-bootcamp). I wanted to apply my skills to this problem that had been a part of my life for years.

- Situation
	- Personal anecdote
	- Background on wildfire risk
		- Cost of wildfires in 2019 or 2020 -> up to $13 billion 2020
	- Other examples of wildfire [[modeling]]

## Scientific background
In order to understand the problem, we have to turn to the field of **pyrogeography,** the study of the geographic distribution of wildfire. When I went to college to get my degree in Environmental Science, I learned the basics of this field, and that there are three main considerations when it comes to understanding fire risk: fuel, climate, and terrain.

Fuel is a pretty obvious one. In areas where there's a lot of dead wood to burn, fires will be more likely to start, and may grow more quickly than in other areas. 

Climate is also clear. In areas that have lower than usual humidity, or higher than usual temperatures, fires would be more likely and more intense.

Terrain is a more interesting variable. Fires tend to spread more quickly when travelling uphill, and fires are also a lot more difficult to put out in hilly areas, meaning that fires here qualify as higher risk than in flat, more easily accessible areas.

I wanted to establish proxies for all of these features so that I could take them into account when estimating fire risk.

- Science of wildfires
	- Climate
	- Terrain
	- Fuel

## Project tools

- Tools
	- Packages I used
		- [[Pandas]] and [[NumPy]]
		- [[matplotlib]]
		- [[streamlit]]
		- [[Scikit-Learn]]
		- [[SQL|SQLite]]

## Methods
I found a dataset of 1.88 million geo-referenced US wildfires on [Kaggle](https://www.kaggle.com/rtatman/188-million-us-wildfires). This would serve as my target feature. Of course, this needed substantial reformatting since this didn't provide data for any county that *hadn't* had a wildfire, only having records of existing wildfires. Additionally, there were limited data for eastern states, forcing me to narrow my analysis to the western United States. I imported this data using SQLite.

As for my predictor features, I retrieved data from multiple sources. I was able to collect climate data from [NOAA](https://www.ncdc.noaa.gov/cag/county/mapping), terrain data from the [USDA](https://www.ers.usda.gov/data-products/natural-amenities-scale.aspx), and fuel data from the [US Forest Service](https://apps.fs.usda.gov/fia/datamart/). After stitching these all together, I had a pretty good picture of the variables that I was working with across the western US. 

I used a variety of models in an iterative process, but the most powerful model I found was the Extra Trees Classifier from the scikit-learn package. This algorithm is a variant of the Random Forest, meant to further reduce variance by randomly changing the cutoff point at each node in each decision tree. For more information on the Extra Trees algorithm, I recommend [this article](https://towardsdatascience.com/an-intuitive-explanation-of-random-forest-and-extra-trees-classifiers-8507ac21d54b). 

One of the most important aspects of this classifier tool that I wished to build would be its flexibility. I wanted a user to be able to raise or lower the threshold when it came to what fire size they wanted to pinpoint. This was because different fire suppression tools have different availabilities and therefore are going to be best suited for different severities. When deploying fire teams, it makes sense to check out all the small, medium, and large fires that are predicted to occur. However, when distributing larger, more expensive resources like airplanes and helicopters, a user should be able to narrow down the results to a smaller, more severe range of fires. 

Because of this, I needed to build in a dynamic tool to prevent [[class imbalance]]. When a user is looking for only the largest fires, these may consist of only a few percent of the total number of observations that the model is trained on. In order to maintain performance, I need to make sure there are enough examples from the positive class for the model to work with. By checking for imbalance during each predictive run of the model, I was able to keep performance higher than it otherwise would have been when looking at very large fires.

Once I was confident that I had adequately tuned the [[hyperparameters]] of my model, and had tested it at various cutoff points, I moved on to deployment. I wanted this tool to be useful for a theoretical user, and so I made the decision to host it online using streamlit. 

Streamlit is a great, simple tool to allow hosting of python code on a web browser. I highly recommend it for anyone looking to deploy models without too much of a hassle. If you want to find more information on how to implement a streamlit deployment, I recommend [their excellent guide](https://streamlit.io/). 

## Results
<center>
	<img src='https://cdn-images-1.medium.com/max/800/0*nMCkjBHjxX5KCqIq.png'>
	</center>

Here we can see an example of the deployed tool. The user can select a cutoff point at a given percentage of the county expected to burn in the upcoming fire season, and then see a result of which counties, in red, are expected to meet or exceed that threshold. 

Below, [[metrics]] display the [[accuracy]] and [[precision]] of the tool to the user. At the model's best, I was able to get a precision score 0.83 and a [[recall]] score of 0.90 when I used a relatively low cutoff point. At the worst, I got a precision of 0.88 and a recall of 0.29 when using a very high cutoff. 

Precision ranged from 0.88 to 0.83, while recall ranged much more, from 0.93 to 0.29. The metrics depended on the cutoff point that the user selected. As the threshold fire size increased, precision improved and recall got worse. This was because 

## Conclusion
This tool exceeded my expectations for what a static dataset, with lots of holes and gaps, could accomplish when paired with basic measures of climate and terrain. I would love to see how this model would work with more fine-grained spatial information and more [[data]] in general when it comes to fire extent and severity.

If you would like to see the guts of this project, head over to my [GitHub](https://github.com/pjn51/modeling-wildfire-risk) where you can see every curve in the road of this project. Thanks for reading, and I hope you leave with a renewed appreciation of the power of nature, as well as our power to understand it using these tools.
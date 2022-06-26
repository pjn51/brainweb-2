---
author: Kiran Prakesh, Lucy Chambers
rating: WIP 
genre: tech
format: article
---
# The Curse of the Data Lake Monster
`LINKS:` [source](https://www.thoughtworks.com/insights/blog/curse-data-lake-monster)
`TAGS`: #article
`AUTHOR:` Kiran Prakesh and Lucy Chambers

---
The authors begin by saying that AI and [[machine learning]] are all the rage these days, and everyone is trying to cash in on their data reserves.

They say that clients often approach them who want to jumpstart their AI initiatives by building a [[data lake]] without thinking about the use-cases. The authors say that these clients believe that by building a robust data infrastructure, use-cases will present themselves later.

Instead, the authors argue that software is best developed in "thin, vertical slices that emphasize use cases and user outcomes, and data-intensive projects are no exception." 

## What are data lakes anyway?
The authors explain that the term 'data lake' implies a centralized repository of data with proper documentation and fine-grained access control, that has been built and maintained by data engineers so that data scientists can consume data and focus on developing ML use-cases while minimizing time spent on [[data wrangling]]. 

Sometimes, the authors say, there is a distinction between data lakes which hold only raw data and "lake shore marts" that hold processed, context-specific data. 

The authors assert that because of this inprecise definition, the creation of data lakes can lead to unplanned scope expansion, overruns, and over-engineering. They say that "it may be that an Amazon S3 bucket" is all we need, instead of a unified [[data]] lake infrastructure.

They say that most organizations would benefit from scope-limited data lakes instead of a single unified data model.

## Build it, they will come
The authors say that the "build it, they will come" mentality is common when dealing with clients who want data lakes. They say that there are multiple possible causes for this.

The authors note that data scientists and data engineers are often on separate teams. They argue that the orientation of data scientists to the business side, and data engineers to the infrastructure and IT side can lead to siloed thinking. Because of this, the authors think that the tendency to consider data lakes as an infrastructure problem emerges. They mention that this is an application of Conway's Law. 

Furthermore, the authors assert that describing the real use-case and "value stream" that the [[data]] lake will address is difficult. They argue that one must discuss this with users and other groups to find a common goal, and warn that this cannot be replaced by a technical approach.

## Pitfalls
The authors caution that designing a data lake in a top-down fashion will result in poor performance. They remind us that 70-80% of the work in building [[machine learning]] applications is [[data wrangling]], most importantly representing the data in a way that makes sense for the use case. 

Therefore, the authors conclude that data preprocessing must exist within the context of a specific [[modeling]] task. Warning us again, the authors say that if we don't approach the construction of a data lake carefully, we will really end up building a data swamp.

## Product thinking for data lakes
The authors propose a bottom-up approach, in which we build the data lake a single vertical slice at a time. Advising us to start with the use cases, the authors apply this to the example of an insurance company that wants to investigate fraud, predict weather patterns, and upsell customers based on the products they already have.

## Before the start
Continuing the example, the authors say that a couple up-front technical decisions have to be made, such as where to host the [[data]]. They recommend having an architectural team to ensure that the overall framework is being applied logically to the whole project. 

## Working through use-cases
In their example, the authors explain that the team knows it has to start small, and picks fraud detection as their first project. The authors say that this team begins by pulling raw customer and claims data into the lake, and then cleaning the data and inserting it into a lake shore mart that sits above the raw data. They say this lake shore mart is designed specifically for this use-case.

<img src='https://www.thoughtworks.com/content/dam/thoughtworks/images/photography/inline-image/insights/blog/data-engineering/blg_inline_curse_data_lake_monster.png'>

The authors remark that now that the initial fraud detection system is in place, the team decides that it could improve the model with more [[data]]. In order to do this, the authors hypothesize, the data team brings in a select few more features, instead of just dumping all the available data into the lake.

Moving on to the upselling, the authors say that this team leverages existing customer data and brings in some new data to create a new lake shore mart for the upselling project. The authors imagine that the team could do a similar thing for the weather prediction project.

<img src="https://www.thoughtworks.com/content/dam/thoughtworks/images/photography/inline-image/insights/blog/data-engineering/blg_inline_curse_data_lake_monster_02.png">

In conclusion, the authors say, a bottom-up process like this, which starts with the use-cases and iteratively adds [[data]] in a controlled way to the lake, can be much better than just trying to clean and organize *all* the data that a company holds. 
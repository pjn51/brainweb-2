# Targeting and location training
on [[22-06-21 Tue]]
with [[Kevin]]

---
This meeting between me and Kevin was dedicated to diving into the location verification and job targeting measurements that we work with. We talked about the purpose of these workflows. 

# Location matching
The aggregation team is responsible for scraping jobs from various sites and posting them on [[Indeed]]. In order to verify that the location [[data]] is correct, we have a [[Location Match queue]] that attempts to verify a few things. First, we want to know the *geotype.* Some jobs are a *single-point* listing, meaning that they're tied to a single location. Other jobs are *multi-point* and are tied to multiple locations. Other jobs have no location at all, such as being an Uber driver or trucker. We want to find the full address if it's a single or multi-point listing.

This queue doesn't just sample randomly from the job pool. There are a few repeat offenders that always have shitty location info, so we exclude them, allowing our graders to focus on a wider variety of tasks. 

When we have these data, we can use [[IQL]] to investigate it and make some quick [[data visualization|visualizations]]. 

Interestingly, there's no method for leveraging RAJ feedback in the location verification workflows. That might be something to explore. 

The team is currently focused on identifying *location blasters*, companies that have a track record of abusing Indeed's algorithm by posting the same job listing in multiple nearby locations in order to increase view counts. 

This grading is done in Appen rather than [[Labeler]]. It's a site where open-source contributors can do [[data annotation]]. There's less oversight and training for this platform, but it's cheaper and suited to simpler tasks. 

# Targeting quality
The big stakeholder for this is the match recommendation platform. They own the "Invite2Apply" product and are responsible for the [[SERP]] homepage. This homepage is powered by a tool called [[recommended jobs platform|RJP]] [3]. This platform relies on a bunch of different match providers [4] that work on recommending based on specific features of the job or the job-seeker. 

The big workflow here is the [[Job to Profile queue]]. It monitors the relevance of recommended jobs based on the job-seeker's profile and user data. The grader is asked a few questions:

1. Is the job relevant to the seeker's previous activity on the site? Reflected in the `jsbehaviorfit` metric.
2. Is the JS qualified? Reflected in `qualifyfit` metric.
	1. If not, why?
	2. If yes, is the job nearby? Reflected in `locationfit` metric.
	3. If yes, is the job better or worse than their current role (based on salary)? Reflected in `betterfit` metric. This is often difficult to answer objectively. 

We can engineer further features from the data generated by this process. We use a metric called `profilefit` which is a combination of `jsbehaviorfit`, `qualifyfit`, and `locationfit`. 

Using these features, we can create reports that compare the performance of the different match providers. These metrics are released in a monthly newsletter [5]. As technical analysts, we can dive into the very bad matches to see what's going wrong in individual [[recommendation]] streams. 

---
1. See the [location match wiki](https://wiki.indeed.com/display/squalops/Location+Match) 
2. [Invite2Apply teak wiki](https://wiki.indeed.com/display/JobI2A/JobI2A+Product+Overview) 
3. [RJP wiki](https://wiki.indeed.com/pages/viewpage.action?pageId=296853528)
4. [Match providers wiki](https://wiki.indeed.com/pages/viewpage.action?pageId=423931180)
5. [Product quality newsletter comparing match providers](https://wiki.indeed.com/pages/viewpage.action?pageId=441710091)
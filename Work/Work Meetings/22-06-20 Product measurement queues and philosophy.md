---
date: 22-06-20
kind: 
with:
---
# Product measurement queues and philosophy
on [[22-06-20 Mon]]
with [[Zandra]] and [[Kevin]]

---
In this meeting, I went over data collection and active processes that the Operations team (within [[Measurement & Tools]]) have built. For more information on this, I was directed to the [team wiki for queue documentation](https://wiki.indeed.com/display/squalops/Measurement+Queue+Documentation). I also have access to the [slides](https://docs.google.com/presentation/d/1D-eeEzq6PC4nVtffBQzSK3gmiFczuAdwH1wERcySoR8/edit#slide=id.gb58abf7d8c_0_331). 

First, we talked about the structure of the team. Kevin is on the Operations side of [[Measurement|PQM]], working on [[data]] collection workflows, which the team calls [[PM queues]].

# PQM queues
There are three areas that we talked about. First up, we discussed the queues related to product quality, the domain of the PQM team. 

There are apparently three subdomains within PQM queries:

1. Query and location relevance
2. Candidate matching
3. Job seeker feedback

## Query and location relevance
The first workflow we discussed was the [[Job to Query queue]], where moderators grade the relevancy of a single job listing against a query. They use this to calculate the [[bad match rate|BMR]] metric. This helps ID low relevant queries and assesses market health. I learned that *Job to Query* BMR is hovering around 10% for the US-en market. 

We moved on to the [[SERP Relevance queue]], which is similar to *Job to Query,* but presents the moderator with a search engine results page (SERP) to grade against the query. This is apparently helpful with uncommon queries. The SERP BMR is dropping, and is currently around 4% for US-en markets.

The third queue is the [[SERP Compariment queue]]. This is much newer, having been released in early 2022. It's similar to the previous two, but instead prompts a moderator to compare our results to those of our competitors such as Google Jobs or Linkedin.

The final workflow for this category is the *Location Match* queue. It produces a metric showing the accuracy of geolocation data. This is tricky, since companies often post duplicate listings so that a larger geographic area is covered.

## Candidate matching
These queues apply to situations where Indeed is targeting a specific jobseeker, advising them to apply to a relevant job. 

The first workflow here is the *Job to Profile* one. A moderator grades a recommendation based on a candidate's resume and other user data. This generates a "good profilefit" metric that measures the performance of this recommendation system. 

Indeed uses multiple [[recommendation]] engines, and this metric is used to compare them to each other. 

## Job seeker feedback
In this subdomain, we take in user feedback from multiple sources, either as numeric scores or textual comments. 

One way in which we use a workflow here is *Report a Job Categorization.* A moderator categorizes text comments into buckets that we can visualize. 

There are other ways that data are generated from feedback, including *SERP Relrating Categorization* and *I2A Relrating Categorization,* both of which do similar things.

There's also a newer way to get feedback during and immediately after the application process, assuming the jobs have interviewed through the Indeed Apply service.

# Technical initiatives
The technical team is taking these data flows and creating [[database|databases]] and indexes, often through [[IQL]] and [[Ishbook]]. My role will heavily involve doing [[exploratory data analysis]] and [[data visualization]] to make sense of these data. 

[[Cronjob|CRON jobs]] allow for automatic data ingestion and refreshes. 
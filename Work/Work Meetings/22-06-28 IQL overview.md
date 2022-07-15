# IQL overview
on [[22-06-28 Tue]]
with [[Dylan]]

---
Dylan and I went over a high-level view of my onboarding process, then we dived into [[IQL]] and some common [[IQL indices]] that our team uses a lot. We discussed where to get [[data]] and [[metadata]], the basics of IQL, the webapp UI, and some neat datasets. 

## Overview of onboarding
He explained that [[Job Seeker Operations]] has their own onboarding, and that's why some of my sessions are irrelevant. They want everyone to have a basic understanding of things like [[DREMR]], [[Waldo]], and job level / account level moderation, even those who won't use those tools.

The things I actually need to know are IQL, [[Cronjob|CRON jobs]], and [[Orc]] (a tool for scheduling CRON jobs).

## Finding metadata about IQL indices
I can get the names of all fields, common filters for each index, the teams that own each index, and more useful information in [[Alexandria]]. 

## IQL basics and web app UI
The syntax is very similar to [[SQL]], except that the [[SELECT statement]] comes last instead of first. There's a sidebar to the left that shows the names of all fields, ranked by how commonly they're used. That's what the green bar represents. 

## Common datasets for my needs
There are a few datasets that the [[Measurement & Tools|M&T]] team uses a lot. 

1. `searchablejobs` provides a dataset of job IDs that are visible to jobseekers. Note that this isn't distinct, and a job that's visible two days in a row will appear twice. 
2. `mobsearch` consists of a dataset of [[SERP|SERPs]] viewed by mobile users.
3. `insightsRajVerbatim` is the [[Report A Job|RAJ]] feedback dataset.
4. `joblevelmoderation` shows a dataset of decisions made by job-level moderators.
5. [[Syed]] has a list of joke / non-serious datasets that [[Indeed]] maintains.

## Miscellanous comments
We also discussed a limitation of IQL, that queries that look for open tickets are based on the day that the index was built.

Also, I asked if teams prefer that I ask questions in their channels rather than sending a DM. He said that in our team, don't worry about it - but if you're asing another team a question, it's probably better to send it in the channel rather than a DM so that those with more bandwidth can answer rather than the random person you chose to DM.

---

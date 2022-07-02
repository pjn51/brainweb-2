# Intro to job level moderation
on [[22-06-23 Thu]]
with [[Erik]]

---
# What is JLM?
Erik showed me the basics of job level moderation (JLM). JLM sends job listings to vendor moderators to identify *quality* policy violations on the individual job level rather than on the account level. These violations are distinct from "risk" which is fraud, while things like bad titles, unclear descriptions, and discrimination falls under the purview of the quality analysts in JLM. 

There are a variety of *origins*, places that feed into the JLM queue. Each origin can be set to fill a percentage of the queue's available space, which is determined by the bandwidth of the moderators. Each moderator can grade something like 450 jobs per day. A [[daemon]] refreshes these queues automatically from [[Waldo]], requiring no manual work.

Interestingly, Erik said that the "golden set" process is paused for JLM, since it was too much of a burden on the moderators relative to the accuracy benefits. 

# How do moderators make decisions?
Erik said that this begins with moderator knowledge of the quality policies in play. The moderators have three options: they can declare a job to be good or bad, or they can escalate it, a process which Erik said rarely happens anymore. They do this all within [[Labeler]]. 

Erik outlined the limitations of these moderators' knowledge. He said that they don't have access to Basestar, Adcentral, and can't differentiate between indexed or hosted jobs. Also, they can't really take action on a deeper level than job description, since that's all they can really see. 

# How does Trust & Safety enforce these decisions?
This is where it got a bit confusing for me. The JLM moderator makes a decision, [[metadata]] is added to the job listing, and based on that metadata, a Waldo filter is applied to the job. 


- how does Trust & Safety (formerly Search Quality) team enforce decisions
	- mod decides -> metadata added to job -> waldo applies rule filters to the job
	- waldo filters: a list of jobs based on metadata
		- different from query since filter contains active AND INACTIVE jobs
		- ModIN filter: full of bad jobs that will have restricted visibility based on an attached rule
		- ModEX filters: full of false positives so that we can exempt certain jobs from a modIN filter
	- GP tags are the concrete metadata that are applied
		- a job hits age desc rule: `GP_B_discrimination` tag applied. 
	- fileters can be tracked or untracked
		- when a filter is tracked for a specific field, it will remove jobs from the filter when that field is changed. Ex: if its flagged for bad title, and the title changes, then it should no longer be in the ModIN filter

# 💥 Action items


---

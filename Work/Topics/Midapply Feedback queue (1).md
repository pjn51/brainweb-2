---
origin: 2022-07-05
aliases: []
---
# Midapply Feedback queue
---
The MidApply Feedback queue is a [[PM queues|PM queue]] that measures jobseeker satisfaction during the application and interview process. This is only active when a listing uses Indeed Apply and hosts interviews on [[Indeed]].

This is a relatively new queue, having been launched in 2022 Q2. 

These comments and their buckets (only for the US market right now) are piped into the `smartapplyevents` [[IQL indices|IQL index]]. 

As of [[22-07 July]], I'm creating a [[Cronjob]] to move Midapply feedback documents into [[Labeler]].

---
1. [Confluence](https://wiki.indeed.com/display/squalops/Apply+Feedback+Comment+Categorization)
2. First reference: [[22-06-22 user feedback queue and policy overview]]
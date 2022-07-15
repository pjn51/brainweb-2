# PQM biweekly
on [[22-07-14 Thu]]
with [[Measurement]] and stakeholders 

---
In this biweekly presentation, [[Lynn]] explained the progress of Project OnetoOne, the effort to discover and eliminate duplicate jobs from [[Indeed]] SERPs. 

She first investigated based on some [[IQL indices]] that found companies with lots of jobs and lots of impressions per job. 

She explained that she was looking for two things: title expansion and location blasting. 

In order to find the former, she compared counts of `jobid` when compared to `external_id`. The former represents listings on Indeed, while the latter connects the Indeed listing to the listing on the company's job site. This can be used to see how many Indeed listings exist per real job. 

She also used [[Waldo]] to do something called "title normalization," a process that appears to cluster very similar job titles per employer. This was something I didn't know we had access to!

Diving in further, she created a Google Sheet where she tracked the number of  locations that the company had, and manually found the number of employees per location. In this way, she discovered that AutoZone has around 94 listings per real job, representing a quantity which is 105% of their total US workforce.

Another top offender, Taco Bell, has 11,000 listings in Mesa, Arizona alone! Across the US, they have a quantity of listings that accounts for 50% of their total workforce. 

---
1. [Running notes document](https://docs.google.com/document/d/1wmbiyUNYcrJgmpwwq-Us2JIyEYqQi5vKNlq8TMStDJ0/edit)
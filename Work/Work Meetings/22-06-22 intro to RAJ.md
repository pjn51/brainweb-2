# Intro to RAJ
on [[22-06-22 Wed]]
with [[Andrew]]

---
In this meeting, Andrew gave a brief overview of how we get [[Report A Job queue|RAJ]] reports, the infrastructure that supports this process, and what we can do with the [[data]]. 

We can get these reports when jobseekers report a job within the listing. We attempt to filter irrelevant or accidental reports upon ingestion. 

Once we have the raw data, we send it into [[Labeler]] for [[data annotation|annotation]] or moderation. This is often done by external vendors, except in the case of low-volume and high-priority moderation, such as human trafficing. These moderation guidelines are set on a country-by-country basis, since there are big differences between the legal systems and job markets around the world. 

We can then use this labeled data to identify problem accounts that will be removed, and even to set long term goals for our products. We can clean up user experiences based on reported issues, or we can change the development of tools and services to better meet seeker needs. 

We can see the results of the Labeling process in a [[Tableau]] dashboard that's updated biweekly. We can also set [[IQL]] alerts to notify us when new data are ready, or upon other triggers. 

Importantly, *we never share specific user feedback with employers.* User feedback must be kept anonymous. 

---
1. Here's the [slide deck](https://www.google.com/url?q=https://docs.google.com/presentation/d/1in0gVnsOOyedssd1fRMRlO2abXQwtHvCTnqPY2deluY/edit%23slide%3Did.p&sa=D&source=calendar&ust=1655919449239215&usg=AOvVaw1DepUH26w2ci9msg2Hi8ip) that Andrew went through
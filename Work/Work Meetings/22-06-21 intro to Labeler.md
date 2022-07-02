# Intro to Labeler
on [[22-06-21 Tue]]
with [[Dan]]

---
Dan and I went over the [[Labeler]] tool. It's a tool for [[data annotation]] that lets us create workflows for graders to label data, often as a way to grade the automated systems that [[Indeed]] is using in one place or another. 

A big source of this data is the RAJ (report-a-job) feedback mechanism. A grader reads a comment left by a displeased user and categorizes it into a bucket such as "spam," "innacurate," or "fraud." 

We use [[CRON job|CRON jobs]] to pump data into these workflows or remove documents if needed. The number of documents varies widely, with some queues containing 10,000 documents a week and others only having a trickle. 

There are various parameters for setting up a queue. We can specify how many graders must agree on a label before it is confirmed, we can select trusted graders to do double-checks on $x$ percentage of documents, or we can create synthetic documents where the true grade is known, and intersperse them into the feeds for the purpose of measuring accuracy. These last documents are known as the *golden set.* 

Dan provided me an exercise to create my own queue that I plan on completing before our review meeting tomorrow afternoon. 

# 💥 Action items
- complete exercise [here](https://docs.google.com/document/d/1PB0PNjpVD9thICm-lcmgYOIvpOClf3T4qGwcg89tiD8/edit)

---
1. Here's the related [wiki](https://wiki.indeed.com/display/ScaledOps/Scaled+Ops+Labeler+Home). It's the old documentation that will get updated sometime.
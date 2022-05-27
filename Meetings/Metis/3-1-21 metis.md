# Metis Notes for Monday, March 1st
`LINKS:` [[metis week 9]]
`TAGS:` #meeting/career

---
## Project 4 Introduction
We can really do whatever we want as long as we pass a few requirements
- Instructor approval
- Try to use more [[data]] than we have in the past

### Deliverables
- Clean and well-documented code
- A six minute video with slides, including a personal introduction

### Timeline
| Date | Deadline / Milestone   |
| ---- | ---------------------- |
| 3-5  | Proposal due           |
| 3-12 | MVP due                |
| 3-15 | Check-in presentation  | 
| 3-19 | Mock presentation      |
| 3-24 | Final presentation due |
| 3-25 | Code due               |

### Tips
Make sure that your project is sufficiently scoped. Don't try and do too much or too little in the time that we have. 

In Leon's opinion, it doesn't matter what the *content* of the project is when it comes to its impact on your resume. What does matter is how well you know what you're talking about. 

## Investigation - introduction to [[genetic algorithms]]
- Overview
	- What is GA?
	- How
- Inspired by [[evolution]], genetic algorithms are a brute-force approach to solving complex problems. 

## Lecture - [[ab testing]]
For this lecture, we have a certain case study. Imagine that you work for a company that sends people emails. Your goal is to get people to open these emails and read them. You could think about this probabilistically.

Imagine we have the true probability that somebody will open an email of variant type X. There is a 0.2 probability that a user will open a type X email. If there's another email, type Y, let's say that theres an identical probability of a user opening a type Y email and a type X email. 

If we run a single experiment comparing X and Y emails, we would see some differences in the opening rate at first, but after running many rounds, we would see that the probability is becoming more and more identical. 

Because of this phenomenon, we have to be very careful when we're sampling a population. We don't want illusions present in the sample to lead us to make the wrong conclusion about a population. To safeguard against this, we should test some hypotheses.

### [[hypothesis testing]]
When talking about hypotheses, we first have to talk about the *null hypothesis.* This is our hypothesis that there is no statistically significant difference between the means of two populations. Related to our email example, this would be the hypothesis that there is no difference between the open rate for email type X and type Y. 

On the other hand, we have the *alternate hypothesis.* This is the hypothesis that there *is* a significant difference between two populations.

In order to compare hypotheses, we have to run many trials and come up with the means of each population. Then, we have to find the probability that we would see such a difference, given that the null hypothesis is true. Basically, we're asking how unlikely it would be for us to see this difference if there really wasn't a difference. If the probability of seeing what's in front of us is low enough, we can support the alternate hypothesis. 

### A Priori
The goal here is to make sure we collect enough data to get a meaningful answer to our research question. There will always be a pressure to collect as little data as possible, because it takes time and money to collect data. However, with too little data, we lose *power*. 

We also need to think about what difference is worth measuring. If there's only a 1% difference between two populations, depending on the use case, the populations might be radically different, or basically the same. 

### Statistical Power
The *P-value* is a classic measure of statistical power. If $\triangle p = 0$, (if the real difference between populations is zero) the p-value is the probability of seeing a difference as extreme or more extreme than ours. This is a measure of type-one error (false positives).

*Power* is another kind of measurement. If we assume that there really is a difference between populations, aka $\triangle p \not = 0$, the power is the probability of detecting that difference with this test. This is a measure of type-two error (false negatives). Power decreases as variance increases within populations, and decreases if we have small effect (small differences between populations).

### Post Hoc
This is for *after the data is collected*. 

We will continue with the email example. We want to identify if a new variation in the email format leads people to open the email more often or not. 

We can use the `statsmodels` library for lots of these tests and metrics, such as p-value and chi-squared test. 

*Fischer's exact test*: If we collect a bunch of data, we're gonna have a total n of successes and failures, broken down into email format A and format B. If we have a total n of data points, there are a finite number of ways this table could be broken down proportionally. Then we can see what the probability of the table breaking down in a certain way, or a more imbalanced way, would be. 

| ...     | Format A | Format B |
| ------- | -------- | -------- |
| Success | 5        | 2        |
| Failure | 5        | 8        |
| Total   | 10       | 10       | 

If the probability of this table being this unbalanced is extremely low, then we have a good reason to believe that there is a real difference between format A and B. 

We can also use ==direct simulation== to perform [[hypothesis testing]]. 

### Summary So Far
There is a real population, but all we have is a sample. We have to compare our sample with all the other samples that we could have pulled. We have to compare hypotheses and make sure to collect enough data to decide which hypothesis is supported. There are various tests to do this. 

### P-hacking
Some people will run test after test until they get a low p-value. This is kind of a dishonest way to do things, and is similar to when we change model parameters to minimize error without using a holdout dataset. 

If we peek at our p-values over and over while messing with the data, we inflate the likelihood of getting a false positive. 

## Speaker - Alice Zhao
- Background
	- Engineering
	- Consulting
	- [[data science]], worked with redfin, others
- Agenda
	- Bootcamp [[data science]] vs real world data science
	- Communicating data and emotion
	- Tips for new data scientists

### Real World Data Science
In our bootcamp, a project often starts with a decree: "You must create a classification algorithm." Then we just google to find a dataset that we can perform classification on. That's not how the real world works at all. 

In the real world, we will be presented with a vague thought or goal, and we have to make it concrete. We will start with an end-user in mind, ask a question, brainstorm, come up with a MVP, and iterate on that. 

We want to find the simplest possible tool to solve the problem, and then we want to make it better and better as time and resources allow. 

==Brainstorming== is a really good skill to have. The value of data science is 5% *using the tool* and 95% *knowing what tool to use*. 

### Interviews
There are two kinds of interviews: case-study interviews, and technical interviews. 

Case-study interviews present you with a problem and an audience, and ask you to identify what kind of data you would need, and what techniques you would apply to the data to solve the question. 

> You are a data scientist for a shipping company. The company would like to figure out a way to decrease the number of employee accidents in the warehouse. How would you approach this problem?

The first thing to do is to determine the end user. The end user here is really the warehouse workers who will be trying to stay safe. Therefore, the first step is to talk to the warehouse workers and see what they need from the process. 

After that, we could perform EDA on the accidents themselves, to see if there are any patterns in when, where, and how accidents happen that we haven't noticed so far. 

### Communicating Data and Emotion
We create data visualizations in order to communicate and invoke emotion. 

> At the end of the day people won't remember what you said or did, they will remember how you made them feel. 
> \- Maya Angelou

The best emotion to invoke is surprise. This gets peoples' attention and has a lot of impact. Other good goals for emotional content include *calm* and *clarity*. 

Don't include visuals just to check a tick-box. Start with the emotional takeaway and customize your visuals in order to achieve this emotional effect. 

### [[career]] Advice for New Data Scientists
 Just do it. Stop overthinking! The interview process is something that you can learn while engaging in. Your GitHub doesn't have to be a library of masterpieces before you apply to the first job. 
 
 Make things public! Just publish your projects and blog posts even if they're not entirely perfect. You will always be the most critical person to see it and most won't notice the imperfections. 
 
 Ask for help. When you have your first project, you're going to want to do it all yourself in order to impress your manager, but that will probably make you mess it up and look foolish. Communication is a valuable asset and you should demonstrate that you are willing to ask for help. 
 
 When you're feeling stuck, create something. Changing your focus towards something that you feel like you're forgetting will help you regain your confidence and  round yourself out. 
 
 Don't compare yourself to others too harshly. Everyone brings something to the table and that's a great thing about data science. There are so many diverse backgrounds that give everyone an edge in one aspect or another. 
 
 Be confident in what you do know, and honest about what you don't know! 
 
 Lean on your colleagues, and look to the Metis community and the data science community more broadly for support and help. The community is very welcoming compared to other fields, and most data scientists would love to share code and expertise. 
 
 ### Q and A
 #### *How can we manage expectations about data science projects from those who are unfamiliar with the problems?* 
 
 Go back to the MVP and focus on iteration, rather than just shooting for the stars right away. 
 
 #### *In what ways is the data science field changing?* 
 
 Data used to be harder to come by, and data science used to be its own department. Now we're at the point where data scientists are integrated into all the parts of the business. Roles are getting more specialized and focused. 
 
 #### *What are the most troubling or stressful situations you've been in and how did you handle them?* 
 
 Being the first data scientist at a company is stressful. You have to figure out how data science will fit into the organization. It's really important to demonstrate your value in those situations or else the company will fire you. Also, [[data ethics]] are another troubling issue with the field. More and more people are spending time thinking of what limitations we need to have in the pursuit of data. 
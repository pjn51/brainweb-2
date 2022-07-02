# Orc training
on [[22-06-30 Thu]]
with [[Yan]]

---
In this meeting, Yan walked me through the basic [[pipeline]] process that [[Indeed]] uses to get [[CRON job|CRON jobs]] running. It was a little confusing, but I'm sure I can pick it up after repeat exposure to these ideas and tools.

Basically, Yan said, [[Orc]] is an [[internal Indeed tools|internal Indeed tool]] that hosts [[CRON job|CRON jobs]]. It's useful to have such a tool since the [[Measurement & Tools|M&T]] team has like 30+ jobs going currently.

## Overview of pipeline process
Yan described the process, referencing a document that outlined it. ^1
First, we begin by using a tool called [[Penelope]]. This tool creates a [[GitLab]] repository for our CRON using some premade scaffolding. Then, we ought to do some local testing to make sure the job is actually working.

Once we're confident the tool is working, Penelope can set up a [[Jenkins]] pipeline that will deploy our code to [[Orc]] where it can actually run. 

Yan clarified that Jenkins is an online task runner that can read our repository, run some tests, and build an executable to deploy. It logs in to the server and runs the code there. He said this was known as a [[continuous integration, continuous deployment|CICD]] tool, standing for "continuous integration, continuous deployment."

## Orc details
Yan noted that there's more than one environment in Orc. There's a production and QA environments. When we make an Orc job, we need to make it in QA and see that it's working, before repeating the process to make it in the prod. environment. Also, jobs cannot read [[data]] between these environments I think.

He went into detail on how we actually create an Orc job, a lot of which went over my head. The basics are that we have to specify a few things:

1. We declare which project we're running
2. Which datacenter to use
3. What date to reference
4. How often to run (the period)
5. What memory resources and compute power to take up
	1. Including the docker image
6. The retry policy (for failure of the CRON job)
7. Command line arguments
8. Environment variables
9. and more...

He said that a lot of these jobs are index builders that upload data to [[IQL]]. He also noted that if we want to get IQL access within our job, we have to connect to a [[Hadoop]] cluster called `skipper`. 

Also, we need to have an environment variable `NEEDS_PROPS=1` in order to use the "secrets manager" called PFC. This is where API keys and other stuff are kept across all projects. Within this manager, the secretes are siloed between datacenters, but we can use an [[AWS]] migration tool if needed.

The team uses [[Kubernetes]], and we can use a thing called "service mesh," which acts as protocols that connect internal Indeed services. This is usually not required.

## How will I use Orc?
Yan said that the [[Product Quality Measurement]] and [[Tooling]] teams basically use Orc in the same way. There are two basic kinds of Orc tasks: index builders and labeler interactors. The former are moving data into [[IQL]], and the latter are used to move data into [[Labeler]]. 

He sent me a google sheet of all the active CRON jobs and their timings. ^2

---
1. [CRON Job walkthrough](https://wiki.indeed.com/display/ScaledOps/Labeler+Cron+Job+Walkthrough)
2. [CRON job google sheet](https://docs.google.com/spreadsheets/d/1o4GYZPpRneMzD3gVXI_eSBtK6v_HEpU4HTxNlE3WXu8/edit#gid=0)
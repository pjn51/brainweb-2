# Tooling team overview
on [[22-06-28 Tue]]
with [[Jesse]]

---
In this short meeting, Jesse and I covered the work of the [[Tooling]] team that operates within [[Measurement & Tools]]. 

They handle more of the technical side like web development, server management, allowing [[Measurement]] to work within these tools and focus on data analysis and visualization. For instance, they created the [[Barkley]] tool. However, they handle building and maintaining some [[IQL indices]] and [[Cronjob|CRON jobs]]. Jesse didn't know why some of these are assigned to PQM while others are owned by Tooling.

Their big project at the moment is BMO. It stands for Better Moderation Output. The goal is to streamline the process for moderators by centralizing the information found on various platforms into one web app so that they can close tickets faster. The tool uses a [[Python]] [[flask]] backend, a [[MongoDB]] datastructure, and a react frontend. ^1

This team is available to help out with anything more technical than data gathering and manipulation, basically.

The team consists of Jesse (him), [[Logan]], and [[Yan]]. 

---
1. https://bmo.sandbox.qa.indeed.net/login
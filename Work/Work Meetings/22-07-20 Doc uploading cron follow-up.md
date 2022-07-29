# Doc uploading cron follow-up
on [[22-07-20 Wed]]
with [[Katie]]

---
Katie advised me to paste the packages that I want to use into the requirements files within the project. She said that I can see that the requirements file is being used for pip verification during the startup process within the manual step-by-step entrypoint.

She said that she thinks I have to add it to `requirements.dev` as well as `requirements.frozen` for it to work both locally (the former file) and when deployed to [[Orc]] (the latter file). 

I asked how I should connect `fetch.py` to `upload_documents.py`, she said she tends to use a [[pd.DataFrame]].

In relation to me getting [[Kerberos]] access, she asked me to set both her and [[Syed]] as watchers on those tickets.

- Copy and paste packages from requirements files in the template
- In the step-by-step entrypoint you can see that the requirements file downloads the correct versions of things
- Gotta add to requirements.dev for local use and requirements.frozen for Orc use
- How to connect fetch to uploader
	- Katie uses dataframe
- Add her and Syed as watchers on those tickets

---
1. [Common cron problems]()
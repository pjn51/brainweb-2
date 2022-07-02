# Intro to account moderation
on [[22-06-21 Tue]]
with [[Andrew]]

---
- Andrew's intro
	- Andrew likes [[Syed]]
	- got an acting and performace degree
	- did edu in Austin
	- Now senior ops analyst in trust & safety
	- studies abuse on the platform, started anto-human trafficing taskforce
- [[Waldo]] rules create automatic [[visibility]] settings
	- 
- Dradis / hosted jobs is the way that emplyers post on Indeed 
- Account moderation
	- T+S reviews jobs to verify that listings are authentic and not fraudulent
	- Is it legit? managed by risk ops within js ops
	- Two levels of moderation as well as RAJ queue
		- For en accounts, tier one and two moderation. Tier two is very few results, and handled internally
		- Many regional queues are low volume and don't have fully staffed moderators
		- Tier one may be vendor, tier two usually internal
- Protcting jseekers
	- majority of fraud is emplyer-based aka the employer is fake or fraudulent
	- Few jobseeker accounts are abusive, but sometimes
	- Very little barrier to create company profile, engenders fraud and requires moderation
- Most fraud comes from dradis but not all
- Process
	- hosted job created --> trigger --> moderation --> decision
- The logs can show you what's up and why employers were sent to moderation queue
- Common triggers
	- nowhere jobs: job postings getting [[visibility]] lowered due to abuse
	- sift score
		- third party [[machine learning]] tool. Used to be the only tool to direct accounts towards moderation
	- nth apply
		- If company gets too many new candidates too fast, moderation will happen
	- location blasting
	- frequent reposting
	- RAJ
		- Two unique user reports within 24hrs will trigger
	- rulebook
		- new tool. trust and safety tool. 
		- we can connect multiple platforms and look at lots of levels at once
- When moderating, ask if the job has a verifiable connection to the company name used, if there are signs of fruad, and the quality of the job postings in the account
	- Business email domain, web presence, ip logins, call log, contact info, etc can establish authenticity
- Moderation tools
	- Basestar
		- Contains queues that accounts are added into so moderators can make decisions
		- "No red flags" says that this is ok for now, but you better not break any rules or you're gonna get moderated again
		- "Ignore" removes from queue, "no red flags" adds a report to the account's history but clears it for this instance
- Rejected employer appeals are handeled by a different vendor. See my [[22-06-21 Disabled appeals + Zendesk]] notes. 

# 💥 Action items


---

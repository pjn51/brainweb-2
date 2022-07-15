---
date: 22-06-15
kind: team
with: JS OPS team
---
# 22-06-15 M&T team meeting
on [[22-06-15 Wed]]
with [[Measurement & Tools|M&T]]

---
This is a 20-person meeting of the whole [[Measurement & Tools]] team. 

# Team intros
- [[Logan]]: TA on tooling. Videogames. 
- [[Dylan]]: team lead for data ops (part of this team apparently). MMA. Dogs.
- [[Zandra]]: team leads for Measurement ops. Dancing. Dog. 
- [[Lynn]]: Reading. Krav Maga. 
- [[Alex]]: Video games. 
- [[Kevin]]: Measurement ops analyst. Disc golf. 
- [[Katie]]: TA on Dylan's team. Cat. Running, cooking. Reading. 
- [[John]]: Dylan's team. Cats. Music. Tennis. 
- [[Will]]: TA on Dylan's team. Wants a cat. Just joined! Florida. 
- Kevin: video games. 
- [[Syed]]: team lead for prod quality. Likes self help books. Biking. 
- [[Yan]]: research engineer. Canadian. Guitar.  
- [[Jesse]]: senior TA on tool side. Motorcycles. Houston. 
- [[Atsushi]]: TA on tooling side. Gym, 2hrs every day. 
- [[Work/People & Teams/Josh]]: TA on Syed's team with me. Just joined!
- [[Megan]]: On Syed's team. Joined in January. Houston. 
- [[Dan]]: Senior ops analyst for measurement. 4 yrs. Dogs. Video games. 
- [[Charles]]: TA on data ops team. Colorado. 
- Me: climbing, biking. Rainy weather

# Knowledge sharing
Every month, somebody volunteers to present something they've been learning about. This is usually technical tools or concepts, but it could be anything job related. Presenters get five store points to buy some merch. 

## Overview of Snowflake (presentation by Alex W)
- More info on Snowflake wiki page for the team. 
- What is snowflake
	- Kind of [[database]]
	- [[MPP architecture]]: massive parallell processing arch. 
	- [[Snowflake]] is a combo of MPP and shared resources (?). Highly scalable, highly fittable
	- It's very much like [[SQL]] in terms of syntax and writing queries
		- It's column-based meaning the data are stored in cols rather than rows. 
	- No "primary indexer," instead "micro partitions" are used
- How to use
	- Onelogin --> snowflake
	- Similar to "blood moon" (?)
	- Has an interface to write scripts and access databases from a big list
	- Provides query performance flowchart so you can see where the memory and time bottlenecks are
	- There's a whole Snowflake team at [[Indeed]]
- [[Python]] / [[Ishbook]]
	- It has it's own version of [[Pandas]] somehow. You can import snowflake results right into a Pandas [[pd.DataFrame]]. 

# 🗓 Next meeting

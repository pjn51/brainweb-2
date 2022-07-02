# Intro to sift science
on [[22-06-21 Tue]]
with [[Andrew]]

---
In this meeting, Andrew and I went over Sift Science. It's a third-party [[machine learning]] tool that basically grades employer accounts on how suspicious they are. It's getting deprecated soon and replaced with an internal tool called Rulebook, but there's no telling when that will happen. 

The tool returns a score from zero to 100 that represents the likeliness of bad activity. Since the tool tends to produce different scores for different markets, there are country-specific thresholds for either review or outright moderation. 

Sift is integrated into the basestar moderation tool. 

Crucially, this is a secret tool, along with basestar. We aren't supposed to tell anyone about them, even the customer success teams at [[Indeed]] shouldn't be told that we're using these tools. We don't want anyone to figure out the specific things we use to detect abuse, or else they could bypass them. 

---

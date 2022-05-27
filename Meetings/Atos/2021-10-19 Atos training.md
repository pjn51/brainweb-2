# 2021-10-19 Atos training
`DATE:` [[2021-10-19]]
`WITH:` multiple
`TAGS:` #meeting/Atos

---
# Andrew Larson
- Metadata
	- "Instructions" mainly say to grade normally, check them anyway
	- "Request ID" tracks the specific session
	- "Activity time" is just a timestamp
	- "Domain name" is the domain for the user, it's the company that's paying MS for our service
	- "Page" lets us know what page our specific login is on. Useful when trying to locate
	- "Familiar Feature Match Type" is the feature ([[data]] point) that is familiar. "No match" means there's a lack of familiarity. That just means we haven't remembered any info tying the session 
	- "Error No" means the status of the login attempt. Either it will say the attempt succeded, or it failed.This could be "IdsLocked", meaning that the user with this ID was locked out.
	- "Credential Type" is the type of credential that they used to login. Usually password. Password is the easiest to abuse, easier than MFA, etc
	- "Client IP subnet" is the closest to IP we can see. We usually refer to this as IP
	- "Country" is self-explanatory
	- "Organization" tells which org is logging in
- The comment box
	- We have a comment box where we *can* leave comments, or hashtags. This is where you would put \#help. Some use notes more than others, some never use it
	- If we need help, comment \#help and we can go over it later
- General advice
	- We can copy the activity time and use it to find the session
	- Hard to know when to mark "suspicious" or "compromised"
	- The "skip" button is useless and we're just going to accidentally hit it
	- Active vs inactive: when was the last login
	- Frequent vs occasional: how many times have they logged in this way
	- When using a mobile network IP organization, expect to see some weird routing
	- An "unclear" grade is for when there isn't enough data
	- The "user countries" tab shows which countries have been logged in from with strong familiarity
	- When there are two logins at the exact same time, it puts it in reverse order for some reason
	- Spoofed locations tend to be from large cities such as LA or NYC
- Our grading options
	- Compromised
	- Suspicious (seems like bad things are happening, but not enough hard evidence)
	- Unclear (missing data prevents us from grading)
	- Not compromised. Must select a reason such as "normal user behavior," "travel," etc
- IP stats tab
	- Gives 7 days of data from that IP org
	- We can see how many sign-in attempts there were. This shows us if there was an attack going on or something
	- Note that some sites show refreshes as "sign-ins" and other sites require constant recurring authentications. Sign-ins can be more than just a logout or login in the conventional sense.
	- We can see user count and tenant count (domains are tenants)
	- The important thing is to see how many people enter a password wrong. If it's really high, that's a red flag.
	- When `"Is hosting facility" = True`, then we can't rely on the location information. Same for `"Is tor" = True`
- User info tab
	- Shows tenant country and user country, last strongly familiar login
	- Shows the most familiar login quantitatively, low number represents uncertainty overall
- Charts tab
	- Shows things visually
	- All *attempts* not sucessful logins
	- Blank means unknown in general
- User agent stats tab
	- Looking at a specific user rather than the tenant that we saw in the user info tab
	- User agents are easy to spoof
	- We have to look at failed logins from a user agent to see how trustworthy it is

# Ryan Emerson
- History and work style
	- Worked for three years total in this position. Left and then came back recently.
	- They had 8 people when he started, now they have nearly 20.
	- The commute to the office sucked, he prefers working remote.
	- He normally grades around 70 sessions daily. He was doing like 100, but he got burnt out. 
	- He used to do 40 or 50 a day, and was told that he needed to do more.
	- He prefers doing a burst of work and then taking a break.
- Comment box
	- He puts the timestamp in there so he can keep track of it, but he doesn't usually comment anything else.
- Grading with weak baselines
	- These often end as unclear. 
	- We should use some sort of process of elimination.
- General advice
	- There's no need to worry about the "Not compromised reason" dropdown, they don't use it for anything much.
	- Attackers often use legacy logons, since there's less protection.
	- Remember that we only have some period of login information, not the *entire* user history.

# Robert Yang
- Worked at Atos for two years
- He thought that working onsite was okay but remote is great
- Work speed
	- He does around 100 a day, depending on the bucket
	- I should expect a little more than 10 sessions an hour when I get comfortable
- General comments
	- When the timestamp has multiple sessions, use the request ID for the session
	- User agents can be spoofed
	- With IP stats, focus on the date where your session to grade is
	- MNE = shorthand for "member not exist"
	- Many Brazilian services have dynamic IPs so it looks like they're hopping when they aren't
	- BID = shorthand for "browser ID"
- The comment box
	- He likes to use the comment box to explain his reasoning a little bit
	- The other Patrick puts *a lot* of details in the comment box
- His workflow
	- First step is the user info, look at tenant info
	- Look out for specific user agents that has a history of being compromised
	- Then go to the charts
	- Then check the "user agent stats" tab, but this is less important than login behavior and baseline
- Common hints
	- Two quick password changes = suspicious
	- m247 IP organization = toss up
	- Zscaler, [[microsoft]] = often trustworthy
	- Tor = typically suspicious
	- ==When we see "Life Graph" as the app, always grade unclear==. This is one of the ten or so exceptions, which we make based on the needs of the DS team above us. 
	- EDU clients  = frequently compromised
	- BAV2ROPC = legacy user, typically compromised
	- Device ID match = likely trustworthy
	- Subway tenant = used to be really compromised, getting better. Tend to be routed all over the place with little baseline. ==Try to avoid using unclear with this tenant.== 
	- A shift in the OS = concerning
	- A shift in the version = not as concerning, unless it's backwards
	- ==Contoso = it's a fake organization to test the security==
	- When the user is created very recently, we can mark them as \#sameday 
	- An authorization code as the credential = better than a password
- Parting advice
	- Find your flow with the comment box
	- Develop a mental checklist to go through with borderline cases
		- User info
		- Charts
		- IP stats
		- Look at first few sessions to find a baseline
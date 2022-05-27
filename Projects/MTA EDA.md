# Metis Project One
---
# Introduction
This is the note for my first [[Metis]] project. The goal is to perform [[exploratory data analysis|EDA]] and [[data visualization]] on MTA data in order to find where an organization should place a team of 20 signature-gatherers. 

# Initial thoughts
We are just trying to find the stations with the most foot traffic basically. This involves two steps of the [[data science]] workflow:
[[data wrangling]]
[[exploratory data analysis]]

link to data -> http://web.mta.info/developers/turnstile.html

# Metadata
C/A      = Control Area (A002)
UNIT     = Remote Unit for a station (R051)
SCP      = Subunit Channel Position represents an specific address for a device (02-00-00)
STATION  = Represents the station name the device is located at
LINENAME = Represents all train lines that can be boarded at this station
           Normally lines are represented by one character.  LINENAME 456NQR repersents train server for 4, 5, 6, N, Q, and R trains.
DIVISION = Represents the Line originally the station belonged to BMT, IRT, or IND   
DATE     = Represents the date (MM-DD-YY)
TIME     = Represents the time (hh:mm:ss) for a scheduled audit event
DESc     = Represent the "REGULAR" scheduled audit event (Normally occurs every 4 hours)
           1. Audits may occur more that 4 hours due to planning, or troubleshooting activities. 
           2. Additionally, there may be a "RECOVR AUD" entry: This refers to a missed audit that was recovered. 
ENTRIES  = The comulative entry register value for a device
EXITS    = The cumulative exit register value for a device

# Agenda
1. Delete duplicates (RECOVR AUD)
2. New column, traffic = entries + exits per hour (find diff)
	1. First we have to apply a shift to find the previous day's entries and exits
	2. Then we create the new column = entries+exits-prev_entries-prev_exits 
3. Group by daily traffic
4. Rank stations by total traffic over the whole dataset
	1. Break down ranking by the month before the gala is happening

# Presentation
8-10 minutes. Time for Q&A. 
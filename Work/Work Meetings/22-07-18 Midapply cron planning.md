# Midapply cron planning
on [[22-07-18 Mon]]
with [[Lynn]]

---
I'm really thankful for Lynn stepping in to help with this, since there were lots of things I had no clue about. 

She recommended that I break this up into a few tickets. First up, she said I should write a 3pt ticket to go over the requirements with [[Josh]], who's working on the downstream [[Cronjob]]. 

Second, she recommended converting my current 7pt ticket to just working on the [[penelope]] -> [[gitlab]] setup part.

Then, I should worry about local QA and deployment next sprint maybe, or just see how far I get with these tickets, since it's my first Cron.

Lynn basically said that 15 points is typical for setting up a new Cronjob.

This was a pretty scattered meeting, and we started to discuss the way that IQL structures its [[data]]. It was originally in [[Java]], so it was pulling from logs in a weird way. Now they've transitioned to [[Python]] (I think) and there's apparently a webapp where you can send [[shards]] to IQL. 

According to what Lynn said, all the day's new data goes into a single table, and when we backfill data, like adding a new field retroactively for instance, we may lose some of these data. That's why she recommends passing as much as possible into the [[Labeler]] database, since it's more stable. 

As for the export into Labeler, she said that I can basically pass a [[JSON]] right in, and I can use other [[Cronjob|Cronjobs]] for reference. 

Because it's so important to have the right stuff passed to labeler, she recommended that I make a new ticket to get the requirements from [[Josh]]. 

She said that I should probably have a different ticket for local QA, and said that getting the code to push to [[GitLab]] will be a whole thing, since there's a bunch of pre-commit hooks.

---
1. [Lynn's extensive notes](https://docs.google.com/document/d/1cFRiqMgL7T8HQAgRcL8kAJy_UI-MesbVb1TLSMIc3e4/edit#)
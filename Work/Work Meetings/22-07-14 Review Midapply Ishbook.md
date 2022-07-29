# Review Midapply Ishbook
on [[22-07-14 Thu]]
with [[Dan]]

---
Dan walked me through the sampling [[Ishbook]] that I'm going to be automating into a [[Cronjob]]. ^3

This process needs to run every day in the morning, so that documents are loaded into the [[Midapply Feedback queue]] for vendors to grade. It samples a single day of activity. 

He also noted that we should probably make the IQL queries more efficient, and chunk them by 1,000 IDs so that they don't clog IQL as much, especially the ones with subqueries.

I asked Dan how I should deal with the login info for [[IQL]], and he said that there's a team login that we're supposed to use for Crons. 

The code was relatively straightforward, with some IQL queries, cleaning, etc. However, the sampling method was rather confusing to read. Dan said that they have to sample the overall result from IQL so that there is an optimal number of documents in the queue on any given day. That means they want to find the minimum number of documents needed to have a 95% confidence level that the sample is represenative, measured as being within a 5% confidence interval. He gave me a link to another way this has been written more cleanly. ^2

We walked through a few syntactic questions that I had. `iaUid` represents the Indeed Apply unique identifier that is generated per unique application. `ctk` represents the cookie tracking key that is unique per user. Dan noted that a user has one `ctk` per user agent that they're using, but he said he *thinks* that the `ctk` is persistent even when a user clears their cookies. I should ask [[Syed]] about that.

In an aside, Dan explained that the `contrib.fetch` library was developed by the Business Intelligence team at [[Indeed]]. The purpose is to make [[pd.DataFrame]] play nicer with IQL. 

He also said that IQL doesn't like null values. If any columns are null in a row, IQL will skip the whole row. 

I asked what the implementation of this [[PM queues|PM queue]] was, and Dan said that it's purely analytical at this point. It isn't used for automatic moderation at all, but there's apparently a team within [[Job Seeker Operations|JS OPS]] called Apply Ops that wants such a tool. 

Dan also noted that there's gonna be commas in the final result, and I should be careful not to use CSV format since it's gonna get all messed up. He recommended using TSV instead.

Dan also recommended that I check out the RAJ indexbuilder Cron, saying that it's a good spot to source code snippets since it deals with lots of different tools such as [[Labeler]], [[Waldo]], IQL, etc. ^4

He explained that I don't need to worry about the analysis Ishbook, and said that [[Josh]] is working on automating that one and generating an [[IQL indices|IQL index]] from that. 

---
1. [Notes](https://docs.google.com/document/d/1yyifH4ttId4HVfQB3buRm8MKEvlEjfVRjM8qyA1PKNA/edit)
2. [Better formatting for sampling code](https://code.corp.indeed.com/squallops/raj-labeling-cron/-/blob/master/rajlabelingcron/sample_size.py)
3. [Sampling Ishbook (updated)](https://ishbook.sandbox.indeed.net/nb/53908/)
4. [RAJ indexbuilder cron](https://code.corp.indeed.com/squallops/sqmeasure_raj_indexbuilder/-/tree/master/sqmeasure_raj_indexbuilder)
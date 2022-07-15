# Coding lifecycle & best practices
on [[22-07-06 Wed]]
with [[Logan]]

---
In this meeting, Logan walked me through a small change to some [[Cronjob|CRON]] code, from the [[JIRA]] ticket to deployment to production.

We began with the ticket SQMEASURE-4626, an example ticket for a one-line code change that he drew up for this training. 

## Step one: git
Now we turn to [[Git]]. Of course, he mentioned, we should never work in the main branch. Instead, we should make all changes in our own branch, and submit them through merge requests. They use command line git here, so I ought to do a quick refresher on those commands. When using `git checkout`, they make sure the message follows the format `jira/ldap/ticketnum`. That means for this checkout, the message was `jira/lseverin/SQMEASURE-4626`. They do this so that JIRA can automatically append this checkout to the original ticket source.

## Step two: GitLab
Now we move over to [[GitLab]]. He created a merge request for this change, and explained that it's easier to track project progress through merge requests rather than individual commit messages. Reviewing the parameters of the merge, he said that there's a way to assign a reviewer here, but he usually just reaches out beforehand to confirm somebody can do it, then assigns "everyone" so that all the people on the [[Tooling]] team get a notification so they can check it out if they want. He advised me to ask [[Syed]] what the protocol is on the [[Measurement]] team. 

As for code reviews, he said that it isn't meant to expose you as a fraud or criticize you in a big way, it's just nice to get additional eyes on your code so that people can help out. 

## Step three: Jenkins
Since this was an update to an already-deployed [[Cronjob|CRON]], this is the last input we need. From here, [[Jenkins]] is watching the main branch, and will see the change come in and automatically do some unit tests, update dependencies, and push the changes on to production. This is all based on a jenkins file found in the GitLab repository, which was populated upon setup by [[Penelope]]. 

Since the CRON is already deployed, there's no need to use [[Orc]] or [[Penelope]] at all. 

## Other tools
Now we moved on to some other tools that are somewhat related to my work. We can use [[Sourcegraph]] to search for things within the GitLab codebase in a more elaborate way than the GitLab search bar allows us to. We can use [[regex]], and "find-and-replace" style mass merge requests. He gave the example of updating a specific URL across 500 python scripts. 

We can use [[Lufta]] to give ourselves access to [[database|databases]], but we will need to submit a request to get access to sensitive [[data]], such as user information. 
 
We can use [[Lola]] to see the logs for each [[Cronjob|CRON]]. 

Finally, we discussed the Nexus Repository Manager, which is a screening tool for Python libraries that we can use. This is integrated into my machine so that I can just use `pip install` to install stuff, and it knows to try and install things from Nexus instead.

## Misc stuff
He pointed me to the running [[22-07-06 M&T team meeting]] document for code guidelines. ^1
There's also an [[Indeed]]-specific [[Python]] style guide that's very similar to [[PEP 8 (2001)]]. ^2
He linked a document to the meeting specifying more detailed steps for CRON creation. ^3

---
1. [Guidelines google doc](https://wiki.indeed.com/pages/viewpage.action?spaceKey=~cbefus&title=Code+Review+Guide#CodeReviewGuide-BadNaming)
2. [Py style guide confluence](https://wiki.indeed.com/display/Python/Indeed+Python+Style+Guide)
3. [Technical processes new-joiner doc](https://docs.google.com/document/d/1XBw1qEEft0SZuzkzjdiHNHij7H7n2QgYq4i4n7cnnQo/edit)
# Doc uploading Cron template overview
on [[22-07-13 Wed]]
with [[Katie]]

---
This was a very hands-on meeting where Katie walked me through the early stages of creating a [[Cronjob]]. First, we discussed some of the basic Cron overview, and she said that they were going to create a template within [[Penelope]] that could set up a document-uploader Cron (the kind that our team works on often), but since the tool is being depricated soon this never happened. 

Because of that, we can just `git clone` the template repository from [[GitLab]] onto our local machine and set it up.

The Cron is generally divided into two files. There's a fetcher file that retrieves data from [[IQL]] via a query, and then there's another uploader file that sends that data into [[Labeler]] for manual grading.

There are two ways to set this up locally after cloning it, both of which are found in the README of the repository. We can either do the quick way, which is to execute a command that does all the setup behind the scenes, or we can do it line by line.

We proceeded to execute the commands line by line so that we could more easily catch errors.

Unfortunately, our setup was cut short since I need [[Kerberos]] access to finish setup. Katie said that she would send me a link to submit a ticket requesting access, and that we would circle back on this in about a week when I got access.

---
1. [Doc-uploader template GitLab repo](https://code.corp.indeed.com/squallops/jsdataops-labeler-cron-template)
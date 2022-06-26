*Git has three local phases.* When working with [[Git]] locally, we have three phases to deal with.

1. *The working directory.* This is our normal file system that we see in our Finder. There's no version control or tracking going on here.
2. *The staging area.* This is where we put files right before we commit them. We have to tell Git to *stage* files for the commit. This means Git will check to see if each file has been modified since the last commit.
3. *The repository.* This is where all our commits are stored. [[Git commits move files from staging area to repo]]. 

This process begins and ends on our computer, but if we want to share files between computers or have backups elsewhere, we can turn to GitHub. [[GitHub adds a fourth phase to Git]]. 

#idea/compsci 
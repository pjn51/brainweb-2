# Git push moves files from local to remote repo.
In order to update the remote repository with our code that we've changed locally, we pass `git push`. 

However, before we can do that we must check for changed code in the remote repository, using `git pull` to update our local codebase. If there are contradictions with the changes we've made, that will result in a merge error that will have to be manually resolved line by line. 

If our remote repository has multiple branches ([[GitHub branches allow for safe experimentation]]) we must specify which branch we're pusing to. 

---
#idea/compsci 
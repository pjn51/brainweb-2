# Git
---
Git is a standard method of version control, allowing us to create checkpoints for our code. It keeps track of the changes to our code, and allows us to revert to a previous version. 

The system is made up of **commits**. A commit is a time stamp where git will save a version of that code. In order to make a commit, we have to understand the three phases of git

[[Git has three local phases]]. 

> [!example] 
> If you want to use git to preserve some code, we first have to add the code using [[command line]]. We run `git init` to start up git, then we `add` our file in git to stage it for the commit. 
> ```bash
> git add my_code.py
> ```
> If we want to access previous commits, we can use a command called `git log`. This lets us into the log of all the old commits, and we can see them. 
> 
> If we want to reset to an older state of code, we take the correct commit id from `git log` and tell terminal to...
> ```bash
> git reset <insert_id_here>
> ```

# GitHub
Git works well enough for files that live on our computer, but what if we want to coordinate the efforts of many programmers? [[GitHub is designed for collaboration]]! 

[[GitHub adds a fourth phase to Git]]. 

>[!example]
>If you want to connect your local repository to a [[GitHub]] repository, In terminal, move to your local repo. Now, in order to link the local with the remote repo, we run `git remote add origin <GITHUB_URL>` with the URL of the repo we made on github.com. We can make sure this worked by running `git remote -v`. If we get a url back, they're connected. 
>
>After we've made a local commit, and have our code in our local repo, we can push the code to the remote one. `git push origin master`. 
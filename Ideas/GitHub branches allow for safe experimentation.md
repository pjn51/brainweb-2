*GitHub branches allow for safe experimentation.* [[GitHub is designed for collaboration]], and this is a perfect example. 

A branch allows us to develop features, fix bugs, and experiment with new ideas without affecting our production codebase. 

The default branch in new repositories is `main`, and if we don't create any more branches, this is where we will be pushing all our local commits to. 

A common use-case is to have a `production` branch and a `development` branch, where code is written and implemented in the `development` branch, and only code that has gone through rigorous testing is moved into the `production` branch. 

Branches may or may not be protected, meaning that there may or may not be enforced workflows that contributors must follow. 

When we want to move changes from one to another, [[Pull requests merge branches in GitHub]]. 

#idea/compsci 

1. https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-branches
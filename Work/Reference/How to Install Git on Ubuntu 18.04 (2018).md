---
rating: 
author: Lisa Tagliaferri
genre: non-fiction
---
# How to Install Git on Ubuntu 18.04
`SOURCE:` [source](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-18-04)
`TAGS:` #wip #article 

---
> [!info]
> This article is about how to use [[Git]] on a remote server. 

# Introduction
They will tell us how to install and configure Git on an Ubuntu 18.04 server. 

# Prerequisites
We have to have a non-root user with `sudo` privileges. They have some other tutorials for how to get to this point.

# Installing Git with default packages
We can install using Ubuntu's default repositories very fast. This might not give us the newest version of anything, so we could install from source instead, which is covered later in the guide. 

First, we need to update the local package index and then install Git:
```
$ sudo apt-get update
$ sudo apt-get install git
```

We can verify the install:
```
$ git --version
```

If this worked, we can move on to the section on setting up git, and skip the next chapter.

# Installing Git from source
Alternatively, we can compile Git from source which will take longer and won't be maintained through our package manager, but we can get the latest releases and more customization. 

We need to first install some dependencies:
```
$ sudo apt-get update
$ sudo apt-get install make libssl-dev libghc-zlib-dev libcurl4-gnutls-dev libexpat1-dev gettext unzip
```

After this runs, we can download whatever version of Git we want by visiting the Git project on [[GitHub]], at https://github.com/git/git 

We should make sure we're on the `master` branch from here on out. Click **tags** and select the desired git version. 

> [!note]
> I'm going to skip the rest of this section since we're not going to follow this route.

# Setting up Git
Now we want to configure git. We want the generated commit messages to have the correct info, and we can do this by using the `git config` command. 

First, we add our name and email:
```
$ git config --global user.name <my name>
$ git config --global user.email <my email>
```

We can see all the configuration items that have been set:
```
$ git config --list
```

There are other configuration options, but these two are the most essential. 

# Conclusion
Git should now be ready to use on our system. They have some more articles on how to use git effectively, how to use branches, and an intro to open source. 
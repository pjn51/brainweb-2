---
author: Christopher Maiorana
rating:  
genre: STEM
format: article
---
# Setting Up Your Remote Repository With Git (2021)
`LINKS:` [source](https://www.inmotionhosting.com/support/website/git/setting-up-your-remote-repository-with-git/)
#article 
`AUTHOR:` Christopher Maiorana

---
Chris begins by saying that he will tell us how to install [[Git]] in a pre-existing remote server. 

## Using Git to publish files
The author says that Git allows for easy file transfer and sharing. He says that we will be using the Git "Push" command a lot.

## How to add a remote repository to your server using Git
The author runs us through several steps to accomplish this process:

1. Log into your server via [[SSH]].
2. In a convinient location, create a new directory ending with the `.git` extension.
3. Enter this new directory in [[command line]].
4. Run `git init --bare` inside the directory.
5. Go back to the local repository.
6. Enter your working directory and run `git remote add <repo> <user>@<destination>:<path>` where `<repo>` is the repo name, `<user>` is our SSH username, `<destination>` is the host domain or IP, and `<path>` is the path to the repository.
7. Now we can push the contents of the local repo up to the remote one -> `git push <repo> master`.
8. Unless we are using SSH keys, we will be prompted for a password.

## How to pull files from your remote repository
The author explains that we will first have to clone the remote repository to our local machine, and then we can push and pull between the local and remote repositories.

First, he says we must clone the repository --> `git clone <repo> <user>@<destination>:<path>`. He advises us that this will prompt us for the SSH password.

Now, the author continues, we can pull changes from the remote repo --> `git pull <repo> master`.
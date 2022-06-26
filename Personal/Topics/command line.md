# The Command Line
`LINKS:` [Learn more about the command line](https://www.datascienceatthecommandline.com/)

---
Command line often gets overlooked in favor of fancier editors, but it has its uses when it comes to [[data science]]!
- You will have to use command line if your'e working with remote servers, such as Amazon's AWS or working in Google Cloud. 
- You will eventually have to use the command line, so you might as well know how to use it well. 

## Moving around in the command line
Command | Result | Example
---|---|---
`pwd`|print the current working directory| `pwd` would return the current working dir.
`mkdir`|create new dir.|`mkdir new_dir` would create a new dir. called "new_dir"
`cd`|change working dir.|`cd new_dir` would change working dir. to "new_dir"
`..`|move up one level|`cd ..` would move the current working dir up one folder level
`~`|return to HOME folder|`cd ~` would change current working dir to HOME dir


## Making and reading files
In terminal, standard output is referred to as `Stdout`, and any output from a program will trigger this process, appearing inside terminal. 

Command | Result | Example
---|---|---
`echo`|print|`echo "hello world"` prints "hello world" in terminal
`>` |set destination| `echo "hello world" > file.txt` will write "hello world" to file.txt 
`cat`|  read file to Stdout|`cat file.txt` will read file.txt into Stdout
`curl`|download from internet|`curl https://archive.ics.uci.edu/data.data` will pull the data source into Stdout
`cp`|copy| `cp file.txt file2.txt` will create a new file, file2.txt, that is a copy of file.txt
`mv`|move|`mv file.txt file3.txt` will move data from file.txt to file3.txt
`rm`|remove|`rm file.txt` will delete file.txt. You can't undo this!

### Flags
Flags are little postscripts for commands. If we want the command do do something slightly differently, we can use a flag. The standard flag notation is 
`<command> --<flag>`.

For example, if we want to copy a whole directory, `cp` won't let us do that, because this is interpreted as a mistake. If we really want to copy a whole dir, we have to enter `cp --r <directory name>`. The `--r` stands for recursive. We have to use this same flag if we want to delete a whole directory. 

# Getting help
If you need help with a specific command, just enter `man <command>`. This will return pages and pages of documentation about the command. 

# When to use the command line
The command line is good for specific things where a GUI and extra functionality isn't needed. Use the command line when...
- the task involves lots of files
- the task is repetitive
- the task has lots of steps
- the task involves lots of independent jobs that need low overhead.

# Advanced command line
## grep
First, we have to know how to `pipe`. This is how we take the output of command A, and pass it to command B, chaining the commands together. Let's say we want to take a dataset on our computer, and print out all the lines that have a certain keyword of 'abc'. 

```bash
cat data.txt | grep "abc"
```
The pipe (|) is what chains the commands together. 

The command `grep` searches for [[regex]] matches, and sends them to Stdout. We can also do the above process by entering `grep "abc" data.txt`.

## Wild card
If you don't quite know what keyword to enter, or want to enter multiple into grep, you can use a **wild card**. Let's say you had a dir with files called "wxyz.txt", "wxy.txt," and "wx.txt". If you want to return the first only, you could call `grep "abc" wxyz.txt`. But if you wanted results from more files, you could call `grep "abc" wxy*.txt`. This would get results from wxy.txt, and wxyz.txt; but not wx.txt. If you wanted results from all .txt files, you could call `grep "abc" *.txt`

## Word count
```bash 
cat file.txt | wc 
```
This will return the number of lines, words, and characters in a file. 

## Which
`which` will tell you where the file that runs something lives. For example, `which python` would let you know where the file that runs "python" lives. If you had both python2 and python3 installed, this command would let you know which version of the language the `python` command was using. 

## Manipulating data
`sed` is a tool we can use for manipulating lots of data. Here's an example of how we would replace every instance of a keyword "alpha" with another word, "omega."

```bash
sed s/alpha/omega/g data.txt
```
In the above code, `/s` indicates we want to substitute, then we write the keyword we are looking for and the one we want to replace it with, and then we write `/g` to indicate that we want this to be a global replacement in the whole file, data.txt. 

The above code will just print this substituted result to the terminal. What if we want to create a new file with the substitution?
```bash
sed -i .TEST s/alpha/omega/g data.txt
```
The flag `--i` will indicate that we want to put this substitution in a new file, which will be called data.txt.TEST. 

If we want to overwrite the file with the substitution...
```bash
sed -i '' s/alpha/omega/g data.txt
```
This will overwrite data.txt with the new substituted file. 

## Getting data in a script
Create a new file called batches.sh

First, we have to tell terminal to run this as a BASH script. Inside the file, write...
```bash
#1/bin/bash
```
Now we can create a [[loops|for loop]] in order to get ten copies of an online file into our file.
```bash
#!/bin/bash

for i in 'seq 0 10';
do 
	curl https://archive.ics.uci.edu/ml/machine-learning-databases/auto-mpg/auto-mpg.data > data$i.txt
done
```
Note the term `data$1.txt`. The dollar sign means that i is a variable we want BASH to unpack. Now if we run `bash batches.sh`, and then run `ls` to see what's in our directory, we will see that we have 11 files of the data. 

### Cleaning the data
What if we want to use this data in [[Python]]? The data has a lot of question marks, and python prefers to see 'nan' instead of '?'. So lets create another BASH script to do a substitution.
```bash
#!/bin/bash

for filename in $( ls data{0..10}.txt);
do
	echo "Cleaning $filename"
	sed -i "" s/'? '/nan/g $filename
done
```
Of course, we first specify that this is a BASH file, then we create a for loop that executes in each file in the directory that has data0, data1, through data10.txt. Then in each file, we print that we are cleaning the specified file, then we perform a substitution to change all '?' to 'nan'. 

## Rsync
`rsync` is a less bad version of `cp`. `cp` sucks because if connection is lost at any time, or if something weird happens, we have to start the transfer over from the start. This would be really annoying if you were sending a huge file over the internet or something. `rsync` can pick up where it left off if an error happens. 

There are two requirements for using this command
1. You have to use [[SSH]] for internet transfers.
2. Both the startpoint and the endpoint have to have `rsync` installed. 

If you wanted to send a file from one directory to a new directory,
```bash
mkdir test
rsync data.txt test/.
```

It gets more complicated if you want to send a file over the internet. 
```bash
rsync -e "ssh -i /path/to/key.pem" data.txt username@IP_Address:/path/here
```

## CRON jobs
If we have a task that we know must be repeated at a certain time each period, such as moving data from a short term [[database]] to a long term one each month, we can tell terminal to execute a task periodically using CRON. 

Imagine we had a script called `job_manager.sh` that performed this task:
```bash
bash load_data.sh
bash clean_data.sh
```

What if we want this task to repeat every 24 hours? We tell terminal to open the CRON scheduler by calling `crontab -e`. This will open a window:
![scheduler](https://camo.githubusercontent.com/d967a26003b14859438467ee27f29cbdfc454b5e903b3351a3ca48b6b3ce1a69/68747470733a2f2f736d687474702d6e65782e6e65786365737363646e2e6e65742f3830333331332f7374617469632f696d616765732f626c6f672f323031342d30312d33302f63726f6e2d6a6f622e706e67)

So in the editor we might specify `59 23 * * * job_manager.sh`. This tells CRON to execute this script at the 59th minute of the 23rd hour of each day. 

## FIND
With `find`, we have a very useful tool for sorting through all our files. For instance, let's say we want to find all the files in a specific folder that we modified more than nine days ago. We want to print these files to `stdout`. 

```bash
find .\specific_folder\* -type f -mtime +9 -print
```
`-type f` indicates that we want only files, `-mtime` is modification time. Then we just tell it to `-print`. 

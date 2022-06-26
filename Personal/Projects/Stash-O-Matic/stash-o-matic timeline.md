# Stash-O-Matic Timeline
`TAGS:`

---
## Introduction
I'm setting this up so that I have a place to keep my thoughts about this project organized. I can list things sequentially so that I can remember where I'm at on the various sub-tasks of the [[stash-o-matic project]]. 

## [[2021-07-02]]
So far, I've done a bit of thinking about the [[stash-o-matic database]], the [[stash-o-matic model]], the [[stash-o-matic loss function]], and I've also been working on a way to send purchase orders to the Dear inventory management system. That lives in a notebook called `purchase_order_sender.ipynb`. 

I feel like I need to hone in on a simple first goal here, and Dad says that it should be to just send Dear a purchase order that the user can approve and then send to Dear. 

## [[2021-07-03]]
I feel like I really need to narrow the scope of this project, at least initially. Dad is really trying to just set up a tool that automates practically the entire running of a business! I just want to focus on a single thing, preventing sell-outs. That will allow Stashlogix to generate a lot more useful data in the future. 

So let's think about what we concretely need for preventing sell-outs. I need to know three things: I need to know current inventory levels, ideally up-to-date, I need to know average sales per day, and I need to know factory lead time. If I have these three things, I can build a tool that issues an alert when inventory is nearing the time when we expect demand over the lead time period to exceed current stock. 

Dad has numbers that he pulled out of his ass for sales per day, and I could just start with those. Ideally, this could be improved, but the data don't exist yet. Lead time is a constant, that Dad should also know. Finally, current inventory seems like the factor that requires the most work because I want this to dynamically update. 

Now that I think of it, automatically sending a PO to Dear is not the MVP here. The tool could just tell us to order x number of y product, and we could go put that into Dear. So I'll focus on the alert system and not worry about automating that quite yet. 

I've now finished the absolute simplest MVP possible for this system. The user defines the current inventory, the lead time, the daily sales of the item, and a minimum acceptable inventory quantity. And I've deployed this using [[streamlit]]. 

I really need to get Dad to rewrite the code to just send the [[Python]] script to the user's terminal, if that's possible. I want to be able to jump into a streamlit site using the stashlogix dev site. 

## [[2021-07-06]]
Just spoke with Dad and he said that it's important for all the python scripts to be running on the server, not locally. This means that we can't deploy via Streamlit, and we should just use the website. He will give me access to the server console so that I can see error messages when running python there. He wants me to research how to install python [[modules and packages]] on the server, as well as how to create inputs that can be read into a python script from the website. He also said that the best way to identify products is the Dear ID, and I can find current inventory levels within the `dear_products` collection in [[MongoDB]]. Finally, we discussed adding a term related to capital utilization to the [[stash-o-matic loss function]]. 

## [[2021-07-08]]
I got into the server logs, and I wrote the way to do that in the [[stash-o-matic database]] note. Dad wrote a python script to accept text input from the stash website, and now my job is to figure out how to rewrite that code to work with the low inventory alert system. 

Now I'm having issues getting the server to run python scripts, even simple ones like `print('hello world')`. I think the issue is that it's taking too long and I end up trying to get multiple scripts to run at the same time and overload the system. I should be careful to make sure the server doesn't get overrun with too many requests. 

So the code is *really* janky for this deployment. The script will treat print statements as return, and will crash the server if there are too many of them. But Dad is changing the structure so that the code will only return when a 'done' is printed. Which is still weird but I can work with that. 

Now the main issue is that my `reciver()` function in `low_inv_alert.py` isn't working. So that's the next action item. 

Ok, got it working! Now I need Dad to change the names of the text input fields, and probably set up context-specific fields for each python script. 

Now the next step is to attach actual inventory levels to this tool. I can find inventory levels in the `projections` collection in MongoDB, and then make the user input a SKU-location to specify which product we're talking about. I should be sure to remember that this is *projected* inventory levels, not actual current levels. That's something to make sure we keep in mind. 

So that changes the goal here a bit. The new goal is to create a script that scans through all the SKU-locations, and makes sure that we still have time to order more products. If there is a SKU-location that needs a refill within the next month, it should ping somebody, through email or something would be cool. 

Dad also wants me to make the cushion equal to the average sales from the last period, times the cushion input for that period. This would make it a little more receptive to actual sales patterns. 

## [[2021-07-10]]
My agenda today is to check out the `projections` collection that Dad created, and see how I can work with that in Python. 

## [[2021-07-13]]
Great, my data pipeline between Python and MongoDB is broken. So now I have to fix that which isn't exactly thrilling work. This is really frustrating, and I can't figure it out. I think it has something to do with me not shutting down a MongoDB session the right way and fucking everything up. Now I can't get it to connect at all, the connection keeps getting refused. 

## [[2021-07-14]]
I think the issue is that I need to be running code on the server so it has an easier time getting to the [[database]]. Now the challenge is getting the server to run PyMongo. 

Ok, so when I run python from the home directory in the server, pymongo works there. That means that the issue is there must be a different installation of python somewhere else in the server, where pymongo isn't installed!

Hooray! I found out that the server was using a different folder, `/usr/lib/python3.6`, and I made pip install pymongo there using `pip install pymongo -t /usr/lib/python3.6`. And it actually worked! Gotta celebrate the small wins. 

Now the mission is to look through the MongoDB document that I have pulled into python as a dictionary, and see what I really need to extract. That is the SKU-location, and the current inventory. I'm going to put the data structure into [[stash-o-matic database]]. 

Ok but now [[NumPy]] isn't installing right. Ok, I can deal with that later. 

#### Convo with Dad
- My code will have two inputs
	- Document in collection (projection_inputs) --> timeline for every sku-location
	- Other input is just user inputs
- Code output
	- Order this many of this SKU on this date
-  `notes.js` has some project notes in it. Find it in the python_scripts folder in the server.

## [[2021-07-15]]
I feel like I can move much faster when working in a [[Jupyter Notebook]]. I need to create a function that can make the projection timeline readable for all the sku-locations. 

I've been running into some issues, but the good kind of issues that I feel I can make progress on. As of right now, I can create a dataframe with the sku-locations as rows and the dates as columns, but it turns all the data to NaNs for some reason. Also, I suspect that the same inventory data is being put in all rows of the dictionary that I've built that predates the dataframe, so I have to investigate that and make sure that all my nested [[loops]] are working correctly. 

## [[2021-08-16]]
Finally getting back into this project. Let's see where I need to pick up: I have a Notebook that can import the `prediction_inputs` file that I downloaded as a snapshot of the database. It has 92 products in it. Then, I created `sku_list`, which is a list of all SKUs found in the file. 

After that, I created a function called `timeline_creator`. The purpose of this function is to take each SKU and return a datafrfame of the projected sales numbers. This function first creates a dictionary of SKUs + locations. Then, it loops through all the SKUs and appends locations to the SKUs for each location found for the SKU in question. 

So far, `timeline_creator` can only spit out a dictionary with SKU-locations as keys. Let's get to work. 

Basically, the things we need to do can be broken down thusly. For each SKU...

1. Locate the SKU's records within `products`  using `product_finder(sku)`
2. Enter each SKU-location and find sales predictions
3. Create a new series for each SKU-location

I've determined how to reach a single date value for a single sku in a single location:

```python
[In]:  	prod_n = 15
		loc_n = 0
		entry_n = 0
	 	products[prod_n]['locations'][loc_n]['timeline'][entry_n]['endingInventoryUnits']
[Out]:  39
```

So there has to be three levels of looping here: we have to loop through SKUs, then we have to loop through locations within each SKU. Within each location, we have to loop through timeline entries. 

*Fucking finally!* I finally did it. I ended up with a DataFrame of dates along the index, and the different products in each column. I treat different locations of the same product as different products entirely. Now the next test is to see if this actually works in deployment... it will probably not and that will make my head want to explode. 

## [[2021-08-17]]
Today I want to create a tool that can alert the user if inventory for any products are dropping too low. My idea so far is to have a function that takes in the predicted inventory dataframe, and a dictionary of minimums for each SKU. If all the SKUs don't have defined minimums, I'll just substitute some number, like 0 for the minimum. 

## [[2021-09-07]]
I've created a function called `warning_bell()` that tells the user the date on which each product will reach some minimum inventory value. What I really want is a tool that tells the user *when* the product will need to be refilled, using a 30-day default lead time. 

Ok, I've made that tool. The next step is to try and deploy it live, meaning that I'll have to rewrite this code for production, and make sure that the `datetime` and `pandas` modules are gonna work on the server. Fingers crossed. 

By the way, this stuff is found in the `getting_inv` notebook. 

## [[2021-09-08]]
I've put all the necessary code for transforming the [[data]] and alerting the user into a .py file so that we could run it on the server. I still need to figure out how to read the data out of MongoDB live, and I still need to make sure that all these modules are going to work on the server. I feel like I did the live data reading before, so I'm going to review my notes and try to find my previous work. 

## [[2021-09-14]]
Today I'm trying to put the alarm bell software into the server. First, I have to figure out why numpy says it's installed in the server, but the .py file says otherwise. I think it has to do with where the python is executing, vs where I've been installing numpy...

Ugh it isn't working, even when I install numpy in the deepest root, or in the `python_scripts` folder. Still saying that the numpy dependencies are missing. Sad.

## [[2021-09-15]]
Interesting discovery! When I pass...

```python
% python
>>>import numpy
```

...in the terminal within the server, I have a success! But when I repeat the same thing with `python3` instead of `python`, I get an error... so maybe the python version is fucked up? So I just need to make sure that python is running 2.7 when I run .py scripts. 

Aha! The python scripts get executed by the `python3` executable. How do I change that... I asked Steve if we could set up a meeting to talk this through later. 

## [[2021-11-11]]
Ok, after a long hiatus, I'm finally going to get back into the swing of this project. I'm glad that I've recorded my thoughts thus far so that I can pick up where I left off. 

It seems that I'm still stuck on getting numpy installed in the right place. First, I need to ssh into the server and get my workspace set up. 

I used `python` to pass `print(sys.executable)` and found that python is executing at `\usr\bin\python` within the server. I think I remember the whole issue being that I want `python` to execute, and instead `python3` is executing. I wonder how I change that?

Ok, it looks like `python` is running 2.7, while `python3` is running 3.6. Lets just try and uninstall that real quick. 

Ok great, when I go to uninstall that from the root, it says it already isn't installed. Great, so now I need to locate where that is running from and kill it at the source. 

Ok, found the path. `python3` is running from `\usr\bin\python3`. Lets go there. Ok, fuck. How do I make `usr` visible again? Gotta look it up. Oh, I remember, I just have to pass `cd ..` to move up a level and see what's really going on. 

Now I see some issues. There are lots of python versions installed, I can see python 2, 2.7, 3, 3.6, and 3.8. I'm pretty sure that's not good. 

First, let me just try installing numpy within the python 3.8 folder. I have to go back into `usr`, then into `local\lib\python3.8` but then when I try to pass `pip install numpy`, I see that it's already installed at `/usr/local/lib/python2.7/dist-packages`. Maybe I have to uninstall and re-install?

That didn't work. It still installed numpy in the same location. So now the question is: will it be harder to get python2.7 to execute, or to install numpy at another location? I think the latter would be harder apparently, after googling how to change the default install location for pip. 

Ok, I see now that the default version of python, the one that is used when `python` is passed, is the correct version that I want. However, the server is executing the scripts using `python3.6` instead for some reason. I asked Dad about this, and now I'm waiting for a response. 

Alright, I think it's actually working! I added an import test to the `test1.py` file that tries to import numpy, and it worked. That must mean my `inv_pipeline.py` file is broken for some other reason. 

For some reason the server is taking issue with a certain line of my code that works in my local notebook:

```python
sku_loc_name = f'{sku_name}_{loc_name}'
```

I'm trying to recreate the problem, maybe it's specific to it being run in a .py format? I'll pick up here tomorrow by testing this on my local machine. 

## [[2021-11-12]]
Ok, time to log in and get to work. I need to run the `inv_pipeline.py` file locally and debug it. I should make sure to use the same version of python, which is 2.7 while my local default is 3.8. 

Found the error! When I run the script in python 3.8, there's no issue. But in python 2.7, the above code snippet is invalid syntax. Let's see if I can find a 2.7 specific workaround. 

Ok what the absolute fuck. Now the server is executing scripts using python 3.8!!! God damn it. Right after I rewrote my code to be compatible with python 2.7 of course. I guess the only way forward is to figure out why numpy isn't visible across python versions. 

I'm going to try and pass `python3 -m pip install numpy` to install it for python 3 specifically. Unfortunately, python3 doesn't even have pip, and it doesn't even have the `ensurepip` module which is supposed to be built in to python...

Ok, I was able to manually run `get-pip.py` that I downloaded, and then I was able to do `python3 -m pip install numpy`. However, now it's saying that a numpy version already exists in `/usr/lib/python3.6`. That's new. But `test1.py` still fails to import numpy, even though it says that it's using python 3.6.9...

Honestly I'm getting close to just scrubbing all traces of python off of the server and starting over. The installations are just all fucked up. I need to talk to Dad about that. 

Maybe I could use a distribution platform like Anaconda to simplify this somewhat. 

This is really frustrating, but it lets me know that dealing with this sort of stuff is a weak area for me that I could do with some education on. I wonder what this topic is really even called?

I had a phone call with Dad, who explained how when I run a python script on the website, the server recieves a message, a specific *route* processes it, and instantiates a python instance using the `python-shell` [package](https://www.npmjs.com/package/python-shell). He hard-coded the path that will be used to create the python instance, so that it will always be 2.7. He thinks the overall problem is that I'm using relative paths when I pass the `import` statement, and since python is being instantiated from different locations, it can't find the packages that I want to import. 

If I want to examine the way that this instance is created in node.js, I can go to `app/routes/tools.js` and scroll to line 544. That's where the python shell is created by [[JavaScript]]. 

We also talked about getting the inventory data into python, and he said that he can easily get the JSON object passed into the python script in the same way that the various text fields pass the data through. I can follow the syntax on `test1.py` in order to get that data, once he writes the code, which should take just a few minutes. 

## [[2021-11-16]]
Back to the grind. Dad wrote the code to bring the `prediction_inputs.json` object into the python script, but now the code in `test1.py` doesn't seem to be working. It worked the first time that I tried it, but on subsequent attempts the page just loads forever. I'm going to restart the server and see if that fixes the issue. 

Ok, I found out what the issue is. The dataset is being transferred to the python instance as a JSON-encoded string. That means I have to turn it into a dictionary by using `json.loads()`. Should be simple enough. 

This is getting a bit frustrating. The script seems to crash due to an unexpected JSON token whenever I try to do anything, such as find the type of an object, which should be a dictionary anyway, not a JSON object. 

Ok, it breaks whenever I make *any* change to the `main()` function. Just printing "test" causes a JSON error. This sucks, but it's just gonna take *n* number of tries to make it work. Let's go. 

I suspect that it has something to do with the way print statements are compiled and passed to the server. That's the only explanation for the super weird behavior that's happening here. 

## [[2021-11-17]]
Today I want to spend some time thinking about the long term trajectory of this project. Dad has some very abstract ideas about how this could be some sort of business-to-business software product. I can work on this in the note on [[stash-o-matic trajectory]], but for now, I need to do some bug hunting.

I've confirmed that all the print statements are being converted to JSON for some fucking reason. When I pass `print('xxxx')`, I see a JSON error saying that an unexpected character "x" was in position one. When I pass `print('zzz')`, I see the same error, but with "z." This sounds like a post-python issue that I'm not sure how to resolve on my end. It has to do with the way that print statements are handled by [[JavaScript]]. 

Dad reworked the whole `test1.py` script, and laid some new ground rules for my files. I have to treat `print()` statements like `return` and make sure to convert them to JSON before printing them at the end of my script. 

## [[2021-11-18]]
Today I can actually get to work on some new code, which is exciting after a few days of bug fixing. First, my goal is to make sure that the data is being imported in the way that I think it is. I should make a script that can just report some basic summary stats about the data. 

Ok, I wrote a simple script called `summarize_data.py`, but I'm getting a new error. I get an error that says `ERROR: write EPIPE` upon running. After searching that term, it seems this has to do with the HTTP request failing due to a closed connection. 

Let's see if I can isolate the error by just running an extremely simple script. Ok, I'm getting the same error even when all my script does is import some things that were working in `test1.py`. 

Time to let Dad know something is up, but first I'll try running `test1.py` again to see if that script still works. That script is eternally stuck on `routes: post to tools/python` in the server logs, so I'm going to restart the server and see what happens. 

No dice. This is still all fucked up. 

## [[2021-11-19]]
I had a chat with Tyler Lubeck, who was helping me get a job earlier this year. He strongly recommended using some platform like Heroku to host the server instead of what we're doing right now. He also said that I could use flask or something as the method for calling from the server. I didn't understand a lot of what he was saying as far as the pipeline goes, but I'll be looking into what Heroku offers, and following his other advice to look up "How to make a basic todo website flask" or something, and use the things I learned there to create something for this project. 

I went ahead and made a toy flask app, and now I've set up the bones of a flask web app that I could import the data into and work within. This is going to be a *ton* easier than working within the clusterfuck that is the current website. *Maybe* we'll be able to integrate the two in the future, but it's best to keep them separate right now. 

## [[2021-11-20]]
I don't have much time to work today, but I wanted to think through the few main goals that I have for the project in the short-term. I really need to get a link between the MongoDB and the flask app set up. I also need to think about whether or not I need a local database for that flask deployment or not. I suppose I don't if the site can just load the data every time the page is refreshed, but that may take a while. 

I'll just set it up without a local database, then we can see how it works. Now that I think of it, I might *need* a database to send information between the HTML and the Python script. That's how the toy app I made worked. So I might as well just go ahead and do that. 

TODO: go back to that tutorial video and set up a SQLAlchemy database. 

## [[2021-11-22]]
DigitalOcean actually has an article on how to host flask apps: https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps

Dad is still set on integrating Python into the JavaScript environment, so we're going to discuss that over the course of the week. I'm open to getting this done if we're close, but if we find a way to host a flask app on the server that will be a lot easier for me to work on independently of him, allowing him to work on other things. 

I guess Dad sees my project as just one step in a sequence of many operations that need to be performed on the data, and he wants my insights to be integrated into the existing dashboard and tools. That means I have to continue working in this JS-dominated environment. 

The only issue we're having now is that `stdin` isn't working in the way that we think it's supposed to. The script is getting hung up while attempting to use `sys.stdin.read()`, but `sys.stdin.readline()` seems to work. When I resume working, we should try using a `for` loop in conjunction with `readline()` to accumulate the lines and then combine them. However, that might take even more time than `read()` does, since we're doing a loop for every individual line. 

## [[2021-11-23]]
Ok, so my Dad figured out a workaround for the `stdin` issue. He just had the JavaScript pre-python stuff download a copy of the MongoDB that we need, and then my script can just grab the script from the server! Pretty elegant. 

Now the name of the game is setting up version control via git. I need to research how to do this in a remote server, since I've never done that before. 

I found a [tutorial](https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu-18-04) that should help me out. I made sure that the server we have is running Ubuntu 18.04. 

[[How to Install Git on Ubuntu 18.04 (2018)]]. 

First thing, Dad needs to create a non-root user with root privileges:

```
$ adduser steve
```

I'm still confused as to where the files would live while we're working on them. Are they going to be cloned to our local machines and then pushed back up to the server? Or are there going to be mulitple branches living on the server? The former seems more likely, but that creates issues with making sure that the environments are exactly the same for testing purposes. 

## [[2021-12-13]]
Today, I'm branching off a bit. I'm going to do some housekeeping, and set up a `universal_functions` file that we can import to deal with the connection between JS and Python. 

I'm also going to create a [[stash gender classifier]] for their sales information. I'll have that in a separate timeline, since that's a substantially different project from this general one. I think that one will be relatively straightforward and will look good on my resume. 

In order to proceed with that project, I must establish a protocol for linking [[MongoDB]] to the Python shell running on the server. 

## [[2021-12-14]]
Time to get to work with the PyMongo integration. I've built a simple PyMongo script, and there's really only one way to get this to work - just try it and begin fixing the bugs which I guarantee will appear. 

In the welcome message when I [[SSH]] into the server, it says "All ports are blocked except 22 ([[SSH]]), 80 (HTTP), and 443 (HTTPS)." Maybe that means I need to change the port to 22 in my code.

Following [this tutorial](https://indianceo.medium.com/how-to-connect-to-your-remote-mongodb-server-68725a8e53f), it seems like the first step is to create a new user. I was able to access the mongo shell by typing `mongo` in the server command line, but I want to be able to get into MongoDB locally through Compass to see which database I need access to. However, that's not working. I remember my Dad was having some issues with that, so I'm waiting to hear from him. 

## [[2021-12-16]]
Dad created a GitHub implementation of the server which I'll be working through from here on out. Long overdue. 

## [[2021-12-22]]
I was able to access MongoDB through Compass. I should be able to translate this method with the same credentials into PyMongo. 

UPDATE: It's working! That was relatively painless. I'm now able to query MongoDB within my python scripts on the server. I'm getting my Dad to try it in order to make sure that everything works, abstracted from my local device. 

## [[2021-12-23]]
It's finally the day: since I was able to get mongoDB hooked up to the python script, I can actually implement the low inventory warning system automatically!!! This has been a long time coming, so let's get to work. 

I got some error messages that are hard to unpack on the server, so I'm migrating to a Jupyter Notebook in order to speed up the process. 

UPDATE: All done! I finally finished this project, and now all that we need to do is have Dad display the products needing to be refilled on the website. This project spanned six months but we're finally ready to move on to something else. 

## [[2021-12-28]]
Of course, it was a bit too soon to claim victory. It's not working on Dad's machine, and now it isn't even working on mine anymore. Frustrating. In fact, the universal_funcs aren't working anymore!  

Another gem is that I can't even see the error messages since JS is only grabbing the first line, where it says `Traceback (most recent call last):` so I can't even see what's wrong. 

This is a real dillema. I guess the immediate need is a way to display error messages. This must be done by converting them to JSON, which the `output()` function was doing, but that isn't working itself. 

## [[2021-12-29]]
Ok, Dad got it working again. The issue was with the python version we were specifying. He sent me a message with a lot of information: 

1. He's confused about what the dates mean in the alert system. 
2. He wants to pass a parameter that will represent the number of days needed as a cushion.
3. He wants a new output called `purchasesNeeded` that will be alongside alerts. This will be a list of dictionaries, one dictionary per alert. Each dictionary will have the sku, dearID, location, supplier, and dateRequired. 

## [[2021-12-30]]
Ok, let's break down this list into chunks. The first thing I'll work on is redefining the output to just return the date that new inventory must arrive by, given a user-defined cushion of $n$ days. 

I think it would be better to incorporate [[OOP]] here, so I'm going to do that. It will allow me to make changes more easily in the future. 

In order to do this, it would be good to work in a notebook environment, so I'll do that. 

Ok, running into an issue here. For some reason, my notebook, located in the `python_scripts` folder, cannot access the `python_data` folder, which is alongside it. This works on the server, so now I have a conundrum. I can change the file structure, and risk fucking up the server, or I can continue to work in a server environment that is much harder to test things in as I code. 

The idea solution would just be to make my testing notebook work with the current file structure. 

Ok, finally got it to work. Just needed to add an extra dot to the relative path. 

Now I can see that for some reason, the transformed dataframe of the sales predictions only has two rows: one with dates, and the other with inventory level. Each column represents a sku_loc. Also, only one date is represented here. 

## [[2022-01-14]]
I haven't been looking forward to bugfixing this project, but I just have to get started already. It's been nearly two weeks since I worked on it last. Last I was here, I was working on a bug with the script, so let's get it all set up and see what's going on here. 

Ok, making some good progress, but for some reason, I can't add additional attributes to my `Pipeline()` class. I have no idea why this would be. 

Also, the edits that I'm making to existing attributes are not being registered. Weird as hell! I have no idea why this could be. The notebook is running from my local `som_1` directory, which is where the python files are. I'm saving those files successfully, and when I open them, the changes are visible. However, for some reason, my Jupyter Notebook is not registering any changes whatsoever. That's so strange. 

OK! I restarted the kernel and that worked for some reason. Jupyter Notebook must save a copy of the imported files somewhere! Good to know for the future, but still very annoying. 

Next step: get the data to live-import using the Jupyter Notebook as a testing environment. 

## [[2022-01-18]]
I didn't record my full progress last coding session. I think everything is working now, and we should be good to go. I'm happy that I chose to incorporate [[OOP]], since now I have a flexible object that is capable of performing multiple operations without re-coding the infrastructure. 

First up, I'm going to code a simple alert that I can run through the website. After re-reading my Dad's last message, he wants me to build a tool that takes a cushion parameter (in terms of days) and returns the day that a sellout is predicted, minus the cushion parameter. If the cushion is five days, then we should find the sellout date, and return the date five days before sellout. 

Ok, after an hour or so of work, I've got a simple alert running that can return a dictionary of products with a date attached, where the date represents $n$ days before sellout, with $n$ set by the user, with a default of seven. 

Actually, this isn't working. I thought it was all good, but the script isn't finding sellouts correctly. Gotta get back in the mud and figure out why it's just returning the first date in the dataset, regardless of inventory. 

## [[2022-01-20]]
Talked with Dad, he reitereated what he wants now:

> Second, pass another dict next to alerts called purchasesNeeded; will be an array of dicts, with one dict for each alert. each dict should have these properties:  
> - sku in exact same format as was passed to you  
> - dearId in exact same format as was passed to you 
> - location in exact same format as was passed to you  
> - supplier in exact same format as was passed to you (array) 
> - dateRequired: date the new inventory must be received

## [[2022-01-26]]
Time to get to work on the `purchases_needed()` method, but first I want to reconfigure the alert system to use the DearID instead of the current identifier, which is a combination of the sku and the location. This will make it easier to work with the alerts later on. 

Actually, I see now that the Dear ID isn't going to work for this. A given product only has one Dear ID regardless of location. Therefore, I'm still going to have to generate my own unique ID. I'll create an identifier of Dear ID and location name, or I'll just put this on hold.

## [[2022-02-02]]
Finding the supplier is an interesting one. When there is no listed supplier, the `supplier` field is just `[]`. However, when there *is* at least one supplier listed, it's its own dictionary that could have multiple suppliers in it. I need to clarify what this is telling me, and what information is needed for the tool to construct POs. 

Update: apparently I should just pass the whole supplier dictionary for now. That simplifies things.

Now I need a way to fetch the supplier info, which is found in `self.doc_dict` (a dictionary), based on the dear ID + location. Unfortunately, products are organized by integers in `doc_dict`, while they're organized by dear ID + location in the `rolling_avg_alert` message. 

That means I have to iterate through the `doc_dict` and pray that the order never gets fucked up. It would be a lot easier if there was a unique identifier, then I could just search for that. But it's more trouble than it's worth to try and create one on the fly during each iteration.

## [[2022-02-22]]
I called my Dad to jump start work on the next phase of the project. We talked about the current JavaScript code that's being used to run the backend of the website. He explained that it relies heavily on JQuery, which is a library that allows access to the `$` object, which has a ton of methods. The whole library is contained within the `$` object.

He walked me through a couple hundred lines of the current code base, and then explained the major actions that have to be taken from here on out. First of all, we have to create unique purchase orders (POs) for each supplier. However, there's an issue here. Since there are multiple products per supplier, and each product might need to be resupplied on a different date, we have to decide how to aggregate the products and decide on a single date to place the PO.

Furthermore, we also have to incorporate minimum order quantities per product, which will affect the rate of resupply. Finally, we have to make sure there's enough cash on hand, a number that can be found in the website console, in `payload.cashBalanceTimeline.timeline`. 

I've decided to reorganize my notes on this project, since a simple timeline will no longer suffice and I should bring my notes up to the newer standard that I've adopted elsewhere. 

Fundamentally, this project is asking, "[[How can we manage Stashlogix cash-flow?]]"

[[Can I adapt EOQ to be more flexible?]]

I want to think out loud about a question, "[[How can we manage Stashlogix POs?]]" The first question here is when to place an order when there are lots of different products that we get from a supplier. I need to know which product they have the least room for,  

## [[2022-03-03]]
I've had a case of writer's block when it comes to this project. I just need to start tackling the questions, one by one. 

### Question #1: [[How can we manage Stashlogix POs?]]
I think that I should talk to Dad and see how often it's feasable for orders to be placed. If once a month, then we just schedule a refill date based on the most at-risk product, and include every product that's going to hit the specified minimum quantity in the following month, making sure to include a quantity that will suffice until the next order. 

```pseudocode
1 for each supplier:
2	for each product:
3		if predicted to be running low within the period:
4			add quantity needed to make it through next period

5	create PO for supplier
```

I think the above code block is basically what we need for this process. But now I can't find where I wrote down what file to create this in, and what code line my Dad was showing me... Ok, found it. 

## [[2022-03-04]]
We're on the phone looking through the code.

- We could create a UI with checkboxes and stuff that allows the user to edit the recommended PO
- The program should be able to take those edits and assemble a PO. 
- Now that we know the PO, we can keep track of cash on hand and make sure that the PO won't violate any of our rules. 
- There needs to be a way to send a final PO over to the DEAR API. 
- DEAR API documentation: https://dearinventory.docs.apiary.io/

## [[2022-03-07]]
Today I'm having [[2022-03-07 coding session]]. 

## [[2022-03-18]]
I went ahead and created a [GitHub Project board](https://github.com/s-norman/som_1/projects/1) to organize some of my work. I would love to collaborate more closely with Dad on this stuff, but time will tell if he will engage. He's busy with other things so I kind of doubt it. 
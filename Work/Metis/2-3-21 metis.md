# Metis Notes for Wednesday, Feb 3rd
`LINKS:` [[metis week 5]]
#meeting/career

---
We're starting off today with a pair programming problem about [[decorators]]. Later, we have lectures on flask web applications, and a review of the classification assessment that we took yesterday. 

## Ridge office hours
We're reviewing [[gradient boosting]]. 

## Lecture - [[communication and deployment]]
At this point, we're familiar with making and tuning models, but there's a whole other step in the process - model deployment. We need a way to host our models online if we actually want users to be able to access them. 

We will need to use some [[HTML]] to do this. HTML is the bones that structure the sites online. It's basically a way to divide the web page into lots of boxes. CSS changes the way these boxes and their contents *look.*

In addition, we need to understand the role of [[JavaScript]]. We use this language to manage elements on the website, adding personalization and interactivity. This can run on web servers, unlike [[Python]]. 

Since python can't run on web servers, we need something to bridge the gap between the two. This comes in the form of [[flask]]. It's a python library that creates a web server gateway interface (WSGI). Flask translates the web server inputs to something that python can understand, and the other way around.

We can also have python stuff hosted on the cloud. Heroku is one service that will handle the web development stuff for us (for a fee) and we can just give them our python code. This is similar to other services like Google Cloud's App Engine. 

In practice, most of us won't really use these sorts of tools on the job. Most companies have their own processes for hosting tools, and often have other web development teams that will handle all the deployment stuff. But we still need to understand what is happening to our models after we create and tune them. Also, this looks really nice on a portfolio!

### Python implementation
For more details, see `flask_intro.ipynb` in my `onl_ds5` repo. 

We first import flask, and  create a WSGI using default settings.

```python
from flask import Flask

app = Flask(__name__) # create flask instance

```

Then we use a decorator to tell flask to route (as a string) the result of this function. We are routing to the main page, so we leave `route` with `('/')`. If we wanted to route to another page of the site, we would put the extension there. 

```python
@app route('/') # the site to route to. in this case, the main page
def hello_world() -> str:
	
	return 'Hello world!'

```

When we run the above .py file, it will take the output and run it on a locally hosted webpage. 

What if we want to include a whole model?

After we've done all the work of creating a great model, we have to save it. We can use [[pickle]] to save the whole model with all the parameters tweaked. 

Now in python, we create a structure in which the model can output a predicted class for a single observation. This observation will be put in by the end user. 

We can do all this work in a notebook, and then when it's working well we can copy it into a couple .py scripts. We could have an API file with all our functions and a driver file with the flask stuff. 

After we've made a locally hosted app that we're satisfied with, we can turn to Heroku to host our app online for others to have access to. 

## Lecture - [[streamlit]]
- This is another python library that we can use to translate python output into an input for a web server. 
- We can change the formatting using markdown, which is nicer than using raw HTML imo. 
- The streamlit site can also be updated dynamically when our code is updated. 

## Lecture - production vs research
- In the big picture of [[data science]], we can divide the world into *research* and *production*. 
- During the bootcamp, we are just doing research.
- In the real world, we include production
- Examples
	- Model deployment
	- Collecing usage [[data]]
	- Labeling usage data
	- Retraining the model periodically
	- Evaluating the new model
	- Deploying the new model
	- On and on...
- Iterative deployment
	- The above cycle continues forever on deployed models. 
	- The daily responsibilities of data scientists involves all of these tasks

## Classification assessment review
### Question 6
> "You fit a Logistic Regression model that predicts whether a student will pass an exam. The features and their corresponding coefficients are: number of hours studied (0.12) and number of hours of sleep (0.23). Which of the following is the correct interpretation of the coeffieicent for the number of hours studied?"

 I said that one additional hour of studying corresponded to a 0.12 percent increase in the probability of passing the exam.
 
The correct answer was that one additional hour of studying corresponded to a 0.12 unit increase in the *log odds* of passing the exam.

### Question 12
> What score represents the number of correct predictions out of all predictions made?

I said that it was the F1 score, but it was really [[accuracy]]. 

This seems obvious to me now, idk how I got this one wrong. 

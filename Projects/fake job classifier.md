# Fake Job Classifier
---
> [!abstract] 
> This is the blog post for my third Metis project. 

One day about a year ago, I was browsing some job boards when I saw a position that seemed too good to be true. It ticked all the boxes - salary, location, description, qualifications. Of course, I applied, and *very* soon, I recieved a phone call out of the blue. I had been accepted! They were eager to get started on the paperwork. A little too eager, in fact. I did some digging, and became more and more confident that giving any sort of personal information to these people would be a bad call.

As part of the [[Metis]] [[data science]] bootcamp that I recently completed, I wanted to apply my newfound understanding of [[classification]] to see if I could create a tool that would be able to help others avoid my fate. I wanted to be able to classify job postings as fraudulent or genuine, using only data that were readily available as part of the posting.

I found the [EMSCAD](http://emscad.samos.aegean.gr/) dataset, which contained 18,000 job postings between 2012 and 2014 that had been identified as fake or genuine by the University of the Agean in Greece. This would serve nicely as a way to train my [[modeling|model]] to be able to discriminate between false and real postings.

For each job posting in this dataset, I had a good deal of information. I had access to the title, location, department, salary range, company profile, description, qualifications, benefits, and more. I planned to use these as features for my analysis. 

The first step for any data science project, after the [[data]] have been gathered, is exploratory data analysis and [[data]] cleaning. The goal here is to see what patterns we can see on the surface of the data, and to get the data ready for the [[machine learning]] tools that can unpack the deeper patterns. 

In order to do this, I loaded the data into [[Pandas]], and got to work. There were a few things that I noticed right away. First of all, I saw that this was a severly imbalanced dataset. Out of the 18,000 job postings, only 866 were fraudulent. This mean that from a classification standpoint, only 4.8% of the observations fell into the minority class.

The other thing that I noticed was that there were a large number of null values for some of the features. I had wanted to incorporate salary, department, and some other features into my classification, but now it was clear that the only consistent information I had for all the jobs was the job description itself. Seeing as false job posts most likely intend to mimic genuine posts, I suspected that a classifier could have a difficult time telling them apart. Despite this, I decided to continue and let the iteration process determine if more data were needed.

# Embedding
With the [[exploratory data analysis]] competed for now, I moved into the [[modeling]] phase of the project. I use an iterative approach, starting from the simplest methods and tools, and getting increasingly complex as needed by the problem. With that in mind, I applied a count vectorizer to the job description.

A count vectorizer is a method of [[embedding]]. We perform embedding in order to transform text to something that we can apply machine learning tools to. Count vectorization is one of the similest methods for doing this. We create a new feature for every word present in the text, and assign a value to each document based on if that word is present or not. In this way, we can create a vector for each document in our corpus (our collection of documents) and we can use various classification tools to leverage this vector.

After I implemented my embedding method, I turned to [[metrics|metric]] selection. Of course, it's important to be able to "grade" our models to see how well they did in classifying our results. We may be tempted to use [[accuracy]] as our metric, asking what percentage of observations were correctly classified. However, there is a fatal flaw to using that metric for this situation. Remember earlier when I mentioned that only 4.8% of the observations were fradulent job posts? That means if my model classified *all* the observations as genuine, it would have an [[accuracy]] of 95.2%. Therefore, I need a more robust metric to use.

# The ROC curve
I found such a model using the ROC curve. ROC stands for reciever operating characteristic, and the ROC curve shows us the performance of a classifier at various *classification thresholds.* The classification threshold is a hyperparameter that determines when observations are put into the positive class. For us, assigning an observation to the positive class means that we think the observation is fraudulent. 

With a high classification threshold, we make sure that the model is very confident about an observation being fraudulent before we classify it as such. With a low threshold, we put observations that the model is pretty sure of being fraudulent into that class. 

# Precision and recall
The ROC curve plots two additional metrics against one another at various classification thresholds, so we need to discuss these additional metrics first. These metrics are *[[precision]]* and *[[recall]].* Precision is also called the false positive rate. The precision metric fundamentally asks, "How many non-fraudulent jobs does the model falsely classify as fraudulent?" 

Recall is also called the true positive rate. This fundamentally asks, "How many fraudulent jobs slipped past our model and ended up being classified as genuine?"

For some scenarios, it's more important to prioritize recall or precision, and some demand that we balance both metrics. For example, if we were classifying biopsies as cancerous or non-cancerous, it's far more important for us to detect *all* cancerous cells, than it is for us to ensure that no false-positives appear. 

However for our use-case, I think that both metrics are important. Obviously, job searchers want to be confident that the jobs they see on the board are genuine, but we also don't want to be flagging jobs as fraudulent left and right, because then employers may prefer another platform that doesn't have as many barriers to posting jobs. 

# ROC AUC
Now that we've discussed what goes into the ROC curve, we can talk about how this metric is used. By plotting recall and precision against one another at various classification thresholds, we can see how 'well' the model performs at various levels of confidence (various thresholds). By finding the area under the curve, we can find a metric that describes how well the model classified the observations in general. A model that is working perfectly would have a ROC AUC of 1.0, while a total guess would have a score of 0.5. 

# Modeling
Finally, I can now turn to the actual process of model selection. First, I'll go through all the models that I tried out during this stage, and then I'll break down the different phases of pre-processing that I put the data through for modeling. Finally, I'll reveal which model performed the best, and which pre-processing steps yeilded the best results overall.

## Model selection
The first model up to bat was a multinomial naive bayes model from [[scikit-learn]]. This is a [[naive bayes]] classifier for multinomial models. This is a simple probabilistic classifier. If you want to learn more about naive bayes and how it can be applied to classification, I recommend [this article](https://www.analyticsvidhya.com/blog/2017/09/naive-bayes-explained/).

The next model I selected was a [[logistic regression]], also implemented using scikit-learn. The logistic regression algorithm follows the same general idea as a [[linear regression]], but since we're trying to predict a binary class rather than a [[discrete and continuous variables|continuous]] variable, we use a link [[function]] to convert from continuous result to a [[probability]] of class assignment. For more information on how this algorithm works, see [this article on the topic](https://towardsdatascience.com/logistic-regression-detailed-overview-46c4da4303bc).

I also tried out a CART model. CART stands for classification and regression trees. The basic idea is to predict the outcome variable (for us, whether a job post is fraudulent) based on the other features. The way that the CART model does this is to create decision points at which the observations are divided into groups. These decision points cascade into a sort of tree of possible pathways, until the data are divided up into roughly homogenous classes. 

However, I didn't just use a single classification tree, I decided to use [[Random Forest]]. Random Forest is a method for dealing with a shortcoming of decision trees. Trees can become *correlated,* meaning that a single very predictive feature is being used over and over. This can get pretty close to what we want, but ideally we would be extracting information from every feature, no matter how little information we can gain. 

The solution to this issue is found in the Random Forest architecture. Random Forest uses many decision trees, with randomly witheld features at each split. For more information on the benefits of Random Forest, I recommend [this article](https://towardsdatascience.com/random-forest-3a55c3aca46d).

Finally, I used a model known as XGBoost. This model uses *gradient boosted* decision trees. Boosting is a technique where multiple models are run sequentially, attempting to patch weak spots in the previous model. When applied to decision trees, this can lead to a pretty great result. For more on XGBoost and the models behind it, see [this article](https://machinelearningmastery.com/gentle-introduction-xgboost-applied-machine-learning/).

## Pre-processing
First, I ran the above models using just the count vectorized company description as my features. This performed pretty well, but I knew that there were some tricks that I could use to get even more predictive power. 

In order to counter the [[class imbalance]] that I talked about earlier, I used a method known as *oversampling.* When class imbalance challenges our models, we can try and increae the number of observations of the minority class in order to give the model more examples of fraudulent behaviour to discern patterns within. Of course, we only oversample observations within the training dataset, leaving the [[model validation|validation]] and testing datasets pristine so that we can see how well our model generalizes to new data.

I re-ran the models using this oversampled data, and I did see improvements. I wanted to try one final trick before I settled with my results. Up until now, I had only been using the company description for the embedding process. Now, I decided to use *all* the text, and see if I could improve the result of my model. Indeed, I was able to substantially improve the model results across the board by doing this.

## Model results
Now the moment we've all been waiting for, the final results of my models. The best performing model ended up being a logistic regression using the combined-text data, with fraudulent observations oversampled. The final metrics were a ROC AUC of 0.97, with a precision of 0.79 and a recall of 0.78. My precision score means that out of 100 job postings that my model *thinks* are fraudulent, 79 of them actually are. My recalls score indicates that out of 100 *actually fraudulent* job posts, 78 of them were successfully detected by this logistic regression model. 

# Conclusion
I hope that I've demonstrated some of the actual work that goes into getting somewhere on a classification project like this. During my time at the [intensive Data Science Bootcamp offered by Metis](), I heard that being a Data Scientist is more about knowing "which nail to hit" rather than "swinging the hammer," so to speak. I think that's clearly the case here, and I'm glad to have gotten such powerful results to share here. 

I would love to do more investigation into what makes the fraudulent job posts so detectable, and what characteristics unite the fraudulent posts that were able to evade detection. I think that research into this topic could be very valuable, not only for the companies that run job boards, but for all us job seekers that see a position that just might be too good to be true.

If you want to get a glimpse at the inner workings of the code that I used for this project, I encourage you to check out my [GitHub repository for this project](https://github.com/pjn51). Thanks for reading! 
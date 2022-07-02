# Topic modeling for JS feedback
on [[22-07-01 Fri]]
with [[Lynn]], [[Dan]], [[Megan]]

---
This was a really interesting meeting where Lynn walked me, Megan, and Dan through a Google Colab notebook she wrote up to do some exploratory [[topic modeling]] on [[Report A Job|RAJ]] verbatim comments. ^1

In order to get the [[data]] into the notebook, she had to export from [[IQL]] into Google Drive as a CSV, connect Google Drive, and then import the data.

She took a dataset of 400,000 documents and sampled 50,000 from them. Then, she used Top2Vec, a lightweight model built on the Doc2Vec library. ^2

She allowed the model to choose the number of topics, resulting in a granular assortment of around 330 topics. 

Lynn showed us some word clouds to illustrate which topics seemed accurate and which seemed meaningless. The most accurate one was for complaints that the job wasn't really remote. She also showed how you can use `model.similar_words` to give the `n` most similar words to a given keyword. This was used to display the associations the model was creating.

## Limitations of the model
Unfortunately, Lynn said, the model can't really generalize to new data, it would have to re-classify all documents when new ones arrive. This limits our ability to put it into production. Also, the variance is an issue. There was a lot of variance between model runs, and I think this might be related to the [[bias-variance tradeoff]] concept. Perhaps reducing the number of topics would make this variance decrease?

Turning to her past experience, Lynn explained that she was part of a hackathon team that tried to automate the labeling process for a different queue. They estimated that about 30% of the documents could bypass the vendors and be labeled automatically, but they didn't have the expertise to put it into production, or even estimate the time and effort to do so.

Lynn said, in a Slack message after we wrapped up, that if this was to go into production, we would probably use an [[unsupervised learning]] model (topic modeling) to find the buckets, and then use a [[supervised learning]] model to categorize new data into existing buckets. 

## Feedback from Dan and Megan
Dan said that it would be useful to be able to scale the number of topics based on which team was asking. He said that some teams prefer the big picture, while others prefer granularity. He said that one issue with RAJ is that the content is so wide-ranging, and that sometimes people discuss multiple issues in a single report. 

Dan continued, saying that it would be interesting to do topic modeling within one of the more vague buckets that RAJ is using, such as the "bad employer" bucket. Then, we could see if the team is missing sub-categories. 

## Next steps
Lynn said that if I want to investigate this subject further, I should reach out across teams to see what other work people have done with [[NLP]] and user feedback. I was told to ask [[Syed]] for a connection to the [[data science]] teams, which are apparently quite broad.

Dan recommended that I reach out to Laura Jewell, who was doing some NLP related to employer NPS a while back.

Lynn said that I should check out the \#data-science channel in Slack.

I think that I'm going to make a copy of this Collab notebook, and see if I can stabilize the model with a smaller number of topics, or possibly create some metrics to see how much overlap there is between vendor categorization and model categorization.

---
1. [Lynn's Google Colab notebook](https://colab.research.google.com/drive/1qYzEIhZChpc_R528NBzn-wB9i-WYA-Z6#scrollTo=lCiUxlq2BuyT76)
2. [Top2Vec docs](https://top2vec.readthedocs.io/en/latest/Top2Vec.html)
3. [Lynn's notes](https://docs.google.com/document/d/160UndWrJXq965LyGb6NJ38kB2PxoFfN1NIwLNmx0dUA/edit)
# Adjective Assisted Album Aggregation
`TAGS`: 

---
> [!info]
> This is a [[data science]] project I completed, using [[NLP]] tools to create an album recommendation system. 

- Situation
	- Lack of emotional content in album search engines
	- Wealth of scrapable data
- Tools / Method
	- Data from pitchfork album reviews
	- Part-of-speech tagging (dimension reduction)
	- Count vectorizer
	- Streamlit deployment
- Results
	- Screenshot of tool
- Conclusion

## Introduction
When looking for an album, we all recognize that emotional content is important for our choice. However, when we're looking for albums, we can really only search for titles, artists, and genres, which doesn't totally capture what I mean by emotional content. Instead, we have to read through album reviews if we want to understand what feelings that album may evoke. 

I thought that there must be a way around this problem, and I wanted to apply some machine learning tools to this interesting dillema. I realized that it would be relatively easy to get album reviews vectorized, and I wanted to see what tools I could create to allow users to get a faster look at the emotional content of an album than reading an album review would allow.

## Gettting the data
As in any data science project, getting and cleaning the data was the most time-intensive step. I used BeautifulSoup and the requests library to scrape the first 60 pages of Pitchfork album reviews, totalling around 708 albums for this proof-of-concept. 

After getting the raw text of the album, I wanted to perform some form of dimension reduction. I knew that I wanted to describe the emotional content of the albums, so I decided to use TextBlob's handy parts-of-speech tagging abilities to only keep the adjectives from the abum review text. By doing this, I was able to dramatically reduce the number of features that my model would later use, speeding this process up and simplifying it. 

## Embedding
Once I had all of the adjectives and albums arranged in a Pandas DataFrame, I applied a CountVectorizer to the data in order to perform embedding. Embedding is the process of turning textual features into something that is machine readable. CountVectorizer is a very simple method of doing this, where each word becomes its own column and each document has either a zero or a one depending on if the word is found within that document.

This gave me a good basis for a search tool, but it only included exact matches. By incorporating the synonym list in PyDict, I was able to expand the range of adjectives that were searched when a user entered a specific term. For example, when a user searched for "energetic," my tool would now search for albums described as "energetic," "fast," "upbeat," and so on. This worked well, and decreased the number of times a user's search would end in zero results. 

## Final tool
I decided to use Streamlit to create a polished tool that a theoretical user could seach albums with. 

[insert screenshot here]

This tool allows a user to enter multiple adjectives that will narrow down the results to albums whose reviews contain at least one synonym per adjective entered. If you want to know how well it approximates the emotional content of the album, give the one above a listen. If you think that it qualifies as both `scary` and `funny`, then you can see the value in a tool such as this. 

If you're interested in seeing the code that went in to this project, or want to check out other things I've been working on, take a look at my GitHub. 
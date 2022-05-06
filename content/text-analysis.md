---
title: Text analysis
prev: data-description
next: network-analysis
---
In order to cunduct a proper text analysis we first need to clean up the text data. This consisted of removing numbers, and symbols from the text corpus, togehter with using regular expressions to remove patterns of text consituting HTML url embeddings, that some users sometimes would leave in there reviews to reference othe rproducts, we also removed unicode for newline, whitespace, special symbols and tabs. All the text was also lowered. Further more in order to prepare the data for sentiment analysis and TF-DIF + Wordclouds, we removed stopwords, from the corpus. Our prior experince with the defualt stopwords in NLTK, was that is was not enough, so we extended the stopwords from multipe sources among others - some commenly used in SQL quering.  
For the tokenization we used NLTK tokenizer since this is an effective solution. Regarding stemming, we didnt find it fit for our use, among reasons was that the words in the Hendometer is not stemmed.  

For constructing documents to use both for sentiment analysis and later for TF-IDF analysis, we combined all reviews texts belogning to a product as one document, so we ended up with a document for each unique product in among the reviews. 
We use the documents of the products to carry out a sentiment analysis and
cross-reference this to the review score, where we expect to see some correlation
between the review score and sentiment score of the product reviews.


|      |  |
| ---      | ---       |
| ![](/static/images/amazon_score.png) | ![](/static/images/amazon_score.png) |


In order to get the sentiment score of the reviews we use the Hedonometer sentiment score and
take the mean over the document for each product which yields a general sentiment of a product.
We compare this to the score of the review (the 1-5 star rating) corresponding to the 
*overall* variable in the review dataframe for the product.

<img src="/images/mean_amazon_sentiment.png">

As can be seen on the figure above where we have the sentiment score on the y-axis and the 
review score on the x-axis there's a correlation between sentiment and review score which isn't very
surprising as better reviews naturally contains more positive wording. 
<br>
One interesting point to make is that the sentiment of the reviews are distributed around a 
median score which is higher as the score grows, but even for all the 5-star reviews the 
sentiment seems to be normally distributed and so there's quite a vast variety of sentiment
values for the reviews with the same score. This could imply that there are different opinions
on what constitutes a 5-star review or just that the reviewers have very different review styles.

---
title: Text analysis
prev: data-description
next: network-analysis
---
### **Cleaning and Tokenization**
For the text analysis we want to investigate sentiment scores in order to evalute how they compare to the amazon score. This is interesting since it will tells us how good the Hendometer sentiment weights generalize across different text domians. It will also tell os someting about how language is conveyed sorrounding review on amazon food reviews - do people use strong positive/negative language for there reviews?  

In order to cunduct a proper text analysis we first need to clean up the text data. This consisted of removing numbers, and symbols from the text corpus, togehter with using regular expressions to remove patterns of text consituting HTML url embeddings, that some users sometimes would leave in there reviews to reference other products, we also removed unicode for newline, whitespace, special symbols and tabs. All the text was also lowered.  

Furthermore, in order to prepare the data for sentiment analysis and TF-DIF + Wordclouds, we remove stopwords, from the corpus. Our prior experince with the defualt stopwords in NLTK, was not sufficient enough for us, so we extended the stopwords from multiple sources, among other, standard stopwords for SQL quering.  

For the tokenization we use NLTK tokenizer. This is an effective solution that yield a sufficent good result. Regarding stemming, we didnt find it fit for our use, among reasons was that the words in the Hendometer is not stemmed.  

### **Documents and Sentiment score**
For constructing documents to use both for sentiment analysis and later for TF-IDF analysis, we combine all reviews tokens belogning to a product as one document, so we ended up with a list of tokens for each unique product. We also calculate the average score for each product from the all the reveiws, this we call just `score`.  

In order to get the sentiment score of the reviews we use the Hedonometer sentiment score and
take the mean over the document for each product, This yields a general `sentiment_score` of the product.  

We then inspect the distribution of Amazon scores and Sentimet scores by vizualization

|      |  |
| ---      | ---       |
| ![](/images/amazon_score.png) | ![](/images/sentiment_score.png) |

We see that there is a great imbalance in the Amazon reviews scores, a majority of products have very high scores, maybe even alarmingly high amount with the score 5.0.
Looking at the Sentiment score distribution we find that it is looking very normally distributed. We see the mean is located above the neutral score of 5. This is in accordancde with research done on other corpuses using the Hendometer wieghs - [Human language reveals a universal positivity bias](https://arxiv.org/abs/1406.3855)

### **Relationship between Amazon revies scores and Sentiments scores**
We then look at the linear relationship between these two scorings.
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

We can see that there is a linear relationship, we calculate a correlation to be  0.4. Its not a very strong correlation but significant enough.
A explanation for why so many products has such a high score can be found in bias we might have induced ourselves - removing product with few reviews - where one can think that the product have fewer reviews was do to better product was brougth instead.

The general problem seems to be that the Hendometer weights does not scores the reviews as high as the actual given score from the reviewer itself. A explanation could be that the type of language that a person will use for a review is more structured, than a random "statement" from a user on a social network like twitter - here a user is likely rewarded (read: getting likes,shares and retweets) more for making more extreme wordings both negative or positive in order to grab attentions. Whereas for a reviews - a user it maybe more focused on getting facts and specification communicated cleary, and even though a review is a tale of experiences, they might word it in a more formal language in order to archive trust, respect and credibility

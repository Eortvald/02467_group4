---
title: Text analysis
prev: network-analysis
---

First and foremost clean and tokenize the review texts. Everything is lowercased, 
stemmed, stopwords and hyperlinks are removed, as well as backslash commands that 
may appear.

> Since the result of the text analysis is heavily dependent on the preprocessing 
> we actually performed the whole analysis and then went back and changed the 
> preprocessing, realizing that we should use stemming, remove some irrelevant 
> words made the text analysis a recursive proces.

With these texts we made documents for each of the products and used tools we have 
learned in this course to carry out an analysis. We used the documents of each 
product to create superdocuments for each category in our dataset. These 
superdocuments were used to create wordclouds of the different categories using an
ID-TDF approach.

We also use the documents of the products to carry out a sentiment analysis and
cross-reference this to the review score, where we expect to see some correlation
between the review score and sentiment score of the product reviews.
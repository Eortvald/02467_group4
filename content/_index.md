---
title: What is this project about?
layout: single
next: data-description
---
The main idea with this project is to analyze reviews on Amazon fine food products.
Are the reviews useful to determine the quality of a product? Is there correlation
between the review score and the sentiment of the reviews? Are there groups or
communities of users in some product categories and if so, how do the reviews
differ from each community in terms of review text.
The project will therefore mainly focus on social tendencies in Amazon reviews.
The dataset comes from [Jianmo Ni](https://nijianmo.github.io/) and consist of 1.1 millions reviews from 127500 
users on 41320 products. The dataset can be found [here](https://nijianmo.github.io/amazon/index.html) originally
sourced from a release of Amazon review data in 2014. The data is sorted so that only products that have at
least 5 reviews and users that have give at least 5 reviews are in the dataset.
The goal of this project is to outline and analyze review text in two ways.
1. We will compare review score to the sentiment of the review
2. We create communities based on products bought and viewed by the same users
and create wordclouds for these communities to analyse the tendencies based on
these product communities.

In the following sections we will introduce the data in more depth including
the preprocessing of the data. We will introduce and discuss the results of 
the network and text analysis in the network and text sections.


## [Explainer Notebook](explainer-notebook.html)

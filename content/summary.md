---
title: Summary
prev: network-analysis
---

The goal of the project has been to give insight into social and sentimental behvavior of the amazon fine foods reviews and to find out how well the products in amazon fine foods could be divided into smaller communities.

From the text analysis, and especially the sentiment analysis, we found a linear relationship with a correlation of 0.4. The langauage used in all of the reviews has an average sentiment score of 6.25. wich is sligty above neutral, which has been proven to be a oftent seen behavoiur.  
We conclude that a linear relationship is seen between sentiment score and amazon score.


From the network analysis we see that there is a clear tendency for users to either buy or view similar products, hence the high clustering of our network and high modularity when partitioning. And especially, users tend to buy, and mostly view, products within the same category. This is the reason that when partitioning the network of products, using the Louvian algorithm, we see communities that mainly consist of products from the same category. 

Analyzing the top communities in our network has given us an insight into what products/brands within each category/community the users has most to say about. We did this by looking at the most popular words as measured by the TF-IDF and as shown in the wordclouds. We found no surprising results when doing this, but found what products/brands dominates the different food categories as measured by the reviews.




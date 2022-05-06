---
title: Network analysis
prev: text-analysis
next: summary
---
In the network analysis we connect products that have 15 common products also viewed or purchased. So if two
arbitrary products have been viewed or purchased with at least 15 of the same other products
they are connected in the graph.

We will use different analytical tools to see the structure of the network.

We expect to see some groupings products based on the hypothesis that users who view or buy e.g. 
some chocolate products are also more likely to view or buy other 
chocolate products. Nevertheless, the structure of the graph will tell us something
about patterns in the data.

We will give a measure of modularity which is how well the graph can be divided into smaller
communities; here we might see the tendencies that we hypothesize, namely that we can see
communities of e.g. coffee users or generally communities around specific categories.

## **Constructing the Network of fine-food products**
Building the network as described above, we should get nodes that are connected with other nodes of similar type, 
either category. One can imagine for instance a user shopping for tea, viewing or purchasing all kinds of differently
flavored tea; so we might see all kinds of tea connected in the graph.
<br>
Below is an image of the constructed network of Amazon fine-food products.
<img src="/images/nopartition_2200_alsoviewed.png" alt="drawing" width="400"/>

The network above has approximately 3k nodes and 347k edges, meaning an average node degree of 319.

Since we are going to investigate groups of products that are related, we conduct a preliminary analysis of the network to 
see how well it splits into groups, i.e. the network's tendency to cluster.
Below is a histogram showing the distributing of local clustering coefficients as well as the network's average clustering coefficient.
<img src="/images/local_cluster.png" alt="drawing" width="800"/>

We see a general high tendency for the products to cluster, which is aslo what is seen in the image of the network presented above.
This indicates that we can indeed work with and analyze the different clusters in the network. Especially, to see if the clusters is dominated by any specific fine-food category and what words from the user reviews dominates these clusters.

## **Community detection**

To work with the different clusters individually, we have to assign each node a label according to which cluster it belongs to. To do this, we partition the network using community detection. For one of the partitions we simply assign each node a label according to its highest subcategory (e.g. "Beverages" or "Snack foods"). For the other method we use the Louvian algorithm to detect communities. Finally we compare these two and check how well they partition the network into useful communities.

Doing this shows that both ways of creating communities yield a relatively high modularity at around 0.7, with the Louvian being slightly higher and finding fewer communities (9 vs. 22).
Obviously, partitioning using the food subcategories yields communities that only contain products within the same food subcategory, which is nice. But what about the Louvian partitioning? Does it also place products of similar subcategory into the same communities?
The plot below shows how many of each type of product (type meaning subcategory) are located within each community. So for each x-value there are nine bars, corresponding to each community. This way, a single tall bar of a certain color at a specific x-value means that the corresponding community (defined by the color) is heavily represented by products of the type shown at the x-value.

<img src="/images/louvian_comms.png" alt="drawing" width="800"/>

What we can deduce from this plot is that the Louvian algorithm actually find partitions that mostly corresponds to the products' food subcategory. This is also supported by a relatively high Normalized Mutual Information at around 0.8, showing a high mutual dependence between the two ways of partitioning. Also, we can see that it finds products from different but similar categories like "Canned, Jarred & Packaged Foods" and "Soups, Stocks & Broths" and partition these within the same community. Again, this is nice, since we can now treat each community (at least the top 5 in size, which we will be working with), as consisting of products of a certain (or similar) food category.

Now, lets have a look at the network where each node/product have been colored according to its community found by the Louvian algorithm.

<img src="/images/louvian_2200_alsoviewed.png" alt="drawing" width="400"/>

In the image above we clearly see the different communities found by the Louvian algorithm.

## **Analysing reviews from communities**

In the following, we will look at the five largest communities found by the Louvian algorithm. And since, for each of these communities, 90% of the products belong to the same category, we just label each community according to the most occuring fine food subcategory(s). So for example, the largest community from the figure of the colored network, which is the blue one, we just label it as "Beverages", since more than 90% of the products herin is under this category.

Now we can look at all the reviews for the products within each community. To do this we create a document of tokens for each community, where the tokens are from all reviews concerning products within the given community. Then we perform a Term Frequency - Inverse Document Frequency (TF-IDF) on all of these documents and show the words with the highest TF-IDF value for each of the top 5 communities in a wordcloud.

The wordclouds of the top TF-IDF words are presented below with their main representative food category as a title.


Beverages             |  Cooking & Baking
:-------------------------:|:-------------------------:
<img src="/images/beverages.png" alt="drawing" width="800"/>  | <img src="/images/cooking_baking.png" alt="drawing" width="800"/> 

Candy & Chocolate             |  Herbs, Spices & Seasonings
:-------------------------:|:-------------------------:
<img src="/images/candy_chocolate.png" alt="drawing" width="800"/>  | <img src="/images/herbs_spices_seasonings.png" alt="drawing" width="800"/>

Snack Foods & Breakfeast Foods             |  
:-------------------------:|:-------------------------:
<img src="/images/snack_foods.png" alt="drawing" width="400"/>  | 

The words from the wordclouds are in great accordance with the associated dominating food categories for each community. We only see words that are specific for each of the categories/communities and that describe what kind of products are mostly reviewed within these communities. Since the wordclouds are made from TF-IDF, words that are common in all categories, such as "good" and "great" are not in the wordclouds, even though these are by far the most occuring words in the reviews measured by pure frequency. Also, we chose not to use stemmning with means that we are able to display the original words used in the review without causing confusion with stemmed words. However, this also means that some of the wordclouds contain redundant words. E.g. the "Beverages" wordcloud contain multiple variations of K-cups, which does not add anything unique to the wordcloud. But again, this is a tradeoff that allow us to show the original words from the reviews, which we deem important.

It is especially interesting that the wordclouds allow one to get an idea of some of the most popular products/brands and not only what adjectives etc. the users use. For example, based only on the wordclouds we can deduce some very popular brands like Haribo, K-cup, Cheezit etz. Of course one could look at the amount sold of each product and use this as a measure of popularity, but with this analysis and the presented wordclouds, one discovers what products the customers engage the most with (as measured by the reviews), and what products might/might not live up to its expectations (good/bad reviews).



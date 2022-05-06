---
title: Network analysis
prev: data-description
next: text-analysis
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

## Constructing the Network of fine-food products
Building the network as described above, we should get nodes that are connected with other nodes of similar type, 
either category. One can imagine for instance a user shopping for tea, viewing or purchasing all kinds of differently
flavored tea; so we might see all kinds of tea connected in the graph.
<br>
Below is an image of the constructed network of Amazon fine-food products.
<img src="/images/nopartition_2200_alsoviewed.png" alt="drawing" width="400"/>

The network above has approximately 3k nodes and 347k edges, meaning an average node degrre at 319.

Since we are going to investigate groups of products that are related we conduct an preliminary analysis of the network, to 
see how weel it splits into groups, i.e. the network's tendency to cluster.
Below is a histogram showing the distributing of local clustering coefficients as well as the network's average clustering coefficient.
<img src="/images/local_cluster.png" alt="drawing" width="800"/>

We see a general high tendency for the products to cluster, which is aslo whatis seen in the image of the network presented above.
This indicates that we can work with and analyze the different clusters in the network. Especially, see if the clusters is dominated by any specific fine-food category and see what words from the user reviews dominates these clusters.

To work with the different clusters individually, we have to assign each node a label, according to which cluster it belongs to. To do this, we partition the network using community detection. First we assign each node a label according to its main subcategory (e.g. "Beverages" or "Snack foods"), then we use the Louvian algorithm to detect communities, and finally we compare these two and check how well they partition the network into useful communities.

It shows that both ways of creating communities yield a relatively high modularity at around 0.7, with the Louvian being slightly higher and finding fewer communities.
Obviously, partitioning using the food subcategories yields communities that only contain products within the same food subcategory, which is nice. But what about the Louvian partitioning? Does it also place products of similar subcategory into the same communities?
The plot below shows how many of each type of product (type meaning subcategory) are located within each community. So for each x-value there are nine bars, corresponding to each community. This way, a single tall bar of a certain color at a specific x-value means that the corresponding community (defined by color) is heavily represented by products of the type shown as the x-value.

<img src="/images/louvian_comms.png" alt="drawing" width="800"/>

What we can deduce from this plot is that the Louvian algorithm actually find partitions that mostly corresponds to the products' food subcategory. This is also supported by a relatively high Normalized Mutual Information at around 0.8, showing a high mutual dependence between the two ways of partitioning. Again, this is nice, since we can now treat each community (at least the top 5 in size, which we will be working with), as consisting of products of a certain food subcategory.

Now, lets have a look at the network where each node/product have been colored according to its community found by the Louvian algorithm.

<img src="/images/louvian_2200_alsoviewed.png" alt="drawing" width="400"/>

## **Analysing reviews from communities**




---
title: Network analysis
prev: data-description
next: text-analysis
---
In the network analysis we connect products that have common users having viewed or purchased them. So if two
arbitrary products have been viewed or purchased by the same user they are connected in the graph. Each
product must have at least 15 common users having viewed or purchased them in order for them to be connected
in the graph.

We will use different analytical tools to see the structure of the network.

Since the edges of the graph are users who purchased or viewed the same product, we expect to see
some groupings of users who view or buy similar products. This is based on the hypothesis that
users who view or buy e.g. some chocolate products are also more likely to view or buy other 
chocolate products. Nevertheless, the structure of the graph will tell us something
about patterns in the data.

We will give a measure of modularity which is how well the graph can be divided into smaller
communities; here we might see the tendencies that we hypothesize, namely that we can see
communities of e.g. coffee users or generally communities around specific categories.
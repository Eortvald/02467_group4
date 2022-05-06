---
title: Network analysis
prev: data-description
next: text-analysis
---
# Netwoek analysis

## Constructing the Network of fine-food products

In order to analyze the relation between Amazon fine-food products based on the users action, we construct a network accordingly.
<br>
When buidling the network of products we connect products that have been bought and viewed together at least 15 times by the same user.
This means that, if two products (product1/product2) in the network are linked, after buying product1 the user has bought/viewed at least 15 other products that the user has also bought/viewed after buying product2.
<br>
Buidling the network this way, we should get nodes that are connected with other nodes of similar type, either category wise or simply products that are e.g. used together, like pasta and ketchup.
<br>
Below is an image of the constructed network of Amazon fine-food products.
<img src="/images/nopartition_2200_alsoviewed.png" alt="drawing" width="400"/>









In the network analysis we connect products that have common users having reviewed them. So if two
arbitrary products have been reviewed by the same user they are connected in the graph.

We will use different analytical tools to see the structure of the network.

> Since the edges of the graph are users who reviewed the same product, we expect to see
> some groupings of users who review similar products. This is based on the hypothesis that
> users who review e.g. some chocolate products are also more likely to review other chocolate
> products. Nevertheless, the structure of the graph will tell us something about patterns in
> the review data.

We will give a measure of modularity which is how well the graph can be divided into smaller
communities; here we might see the tendencies that we hypothesize, namely that we can see
communities of e.g. coffee reviewers or generally communities around specific categories.


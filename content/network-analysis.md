---
title: Network analysis
prev: data-description
next: text-analysis
---
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


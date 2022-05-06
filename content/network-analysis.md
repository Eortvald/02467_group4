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




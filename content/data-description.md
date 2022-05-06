---
title: Data description
prev: "/"
next: text-analysis
---

The data of this analysis are reviews of Amazon fine food products as well as some 
metadata for the products in the reviews.

<img src="/images/food_front.jpg"/>

The 1.1 millions reviews are loaded into a pandas dataframe. Note that only products and users that have at
least 5 reviews are in the dataset. Each row in the dataframe
corresponds to a review and each column is a variable for the review. Below, we've
included a snippet of the review dataframe. The reviews are from 2000-08-09 to 2018-10-02.

<img src="/images/data_example.PNG" title="Snippet of 2 reviews"/>

The header in each column explains the variables of the review in each row. As mentioned, we also have metadata on the products that are being reviewed. The
metadata contains information about specific products. Including only the product that occur in our reduced data of reviews we have a total of 39320 products.  
For the two datasets we have the following attriubtes:

### Review dataframe
<img src="/images/product.png"/>
<br>

### Meta dataframe
<img src="/images/meta.png"/>


Since we suspect that some of the reviews are made by bots, we exclude these reviews based 
on some common criteria:
* The same userID submitted multiple reviews within seconds of one another.
* The same userID left multiple reviews of the same product.
* Users review different products with the same review/title for the products
* Multiple users making identical reviews for a product.

We choose to be tough on bot-like reviews since the dataset is so large.
For instance this user posted multiple very similar reviews on the same product.
<img src="/images/bot_table.png"/>
<br>  

## **The ten characteristics of big data**
For the Amazon food data set we have here commented on the the ten characteristics of big data.  

1. Big
   * The dataset is very large. It would not be feasible to collect the same amount of data by e.g. surveys. 
2. Always-on
   * Since reviews are constantly being made we simply take data from a specified period, since the
   analysis is not time sensitive.
3. Nonreactive
   * Since the point of a review is for other people to read it, we must assume that the data is not nonreactive.
4. Incomplete
   * Obviously it would be nice to have more information but in this case the analysis was designed to
   fit the data.
5. Inaccessible
   * This data is something that Amazon has released. We wouldn't be able to get this data ourselves since
   Amazon enforces a re-captcha when applying modules like BeautifulSoup to scrape reviews.
6. Nonrepresentative
   * Our data revolves around analysing reviewers. So the users is the population, which they are completely
   representative of. If we were to generalize any results we would have to keep in mind that the users who
   review product might not necessarily be representative of the general population. There are some confounders
   that can affect representation that will be discussed in *Algorithmically confounded*
7. Drifting
   * We cannot exclude the possibility of either population-, behavioral-, or system drift. But since the
   analysis is not time sensitive it shouldn't pose too much of an issue. We can obviously imagine that the
   users change over time, or that the pandemic affected the review score of products or that updates from 
   of Amazon.com could change some tendencies of the reviews. 
8. Algorithmically confounded
   * This is quite an important point to make. Amazon has incentive to make users review as many products
   as possible to increase the user experience on their website, especially positive reviews in order to
   sell more products. There have been stories of sellers offering users double refunds to take
   down negative reviews as these are absolutely detrimental for their products to compete, and there are
   also many stories of users having their reviews deleted, both of which creates confounders in the data.
9. Dirty
   * Amazon tries to regulate bot reviews, at least seemingly. But it is impossible to know what's going on
   behind the scenes in Amazon offices. We must assume that not all reviews are human-made which is why we
   clean the data.
10. Sensitive
    * The data isn't sensitive as it is expected from the user that the reviews are being read.

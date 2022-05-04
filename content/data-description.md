---
title: Data description
prev: "/"
next: network-analysis
---

The data of this analysis are reviews of Amazon fine food products as well as some 
metadata for the products in the reviews. For the reviews themselves we have some 

The XXXXXXXXXXX reviews of XXXXXXXXXXXX products are loaded into a pandas dataframe. Each row in the dataframe
corresponds to a review and each column is a variable for the review. Below, we've
included a snippet of the review dataframe.

<img src="/images/data_example.PNG" title="Snippet of 2 reviews"/>

The header in each column explains the variables of the review in each row. Firstly,
we have an *overall* review score corresponding to how many 'stars' the reviewer gave
the product on a scale of 1-5. The *verified* column is true if the user that reviewed
the product actually has a purchase of the product which is verified by Amazon. 
Next, there's a
*reviewTime* in month/day/year format, a *reviewerID* and *asin* is simply the product
code for the reviewed item. The *reviewerName* is simply the profile name of the user
that reviewed the product. The *reviewText* is the comment and the *summary* is the 
'headline' of the comment and the right-most *TEXT* variable is a combination of 
these two. *unixReviewTime* is the review time in unix (so the number of seconds
since 00:00:00 UTC on January 1st 1970). The *vote* is a variable that contains 
other users' opinion on this specific review. Other users can vote on if a review
is 'helpful' which will show here. *style* contains information regarding 
specifications of the product (weight/volume/6-pack/packaging etc.)
*image* refer to images they may be attached to the review.

As mentioned, we also have metadata on the products that are being reviewed. The
metadata contains information about specific products. We load it in a pandas
dataframe and similarly to the review data, there are XXXXX rows corresponding to 
each unique product. The columns are variables regarding each of the products. We
have the following variables:
*category* contains a category and all the subcategories the product belongs to.
Almost all the products are in the same category "Grocery and Gourmet food". But for 
instance a teabag will have the subcategory "Beverages" and the sub-subcategory 
"Coffee, tea and XXXXXXXXXX". *title* and *description* contains the title
and description of the product. We also have the same *asin* product code.
*also_buy* contains the *asin* product codes for 
products that users have also bought alongside this product, and likewise with 
*also_view* that contains the *asin* code for items that we're also viewed. The 
metadata also contains *brand*, *price*, *similar_item*s as well as hyperlinks to
the images in the product site named *imageURL* and *imageURLHighRes*. Some products
have *details* e.g. dimensions of the product. Likewise, some products have *feature*
containing e.g. certifications of the product.
There's a *rank* of the products listed after how well they sell, a *date* of when
they were listed and *main_cat* which is mostly grocery since this is the category 
we're the most interested in. Lastly, we have a *tokens* connected with each unique 
product.


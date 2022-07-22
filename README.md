# Amazon_Vine_Analysis

## Overview

Analyzing Amazon reviews in AWS with Spark(PySpark) and SQL

We will be working with BigMarket who's a company that helps bussinesses optimize their marketing efforts.<br/>
Our cliente $ellby requests us to analize a large catalog of products on a leading retail website and they want to know
how the reviews of their products compare to the reviews of similar products sold by their competitors.<br/>
They are also interested in enrolling in a program that gives out free products to select reviewers but they want to know if it's worth the cost.<br/>
We will be using Spark(PySpakr), AWS, SQL and NLP to analize the reviews and report our findings.

The information was downloaded from the Amazon Review datasets and the dataset to analyze contained information about Mobile and Electronic devices sold in the US. This dataset contains reviews from Amazon Vine program.  <br/>
Due the amount of information stored in the dataset, we created a AWS database for PostgresSQL and then loaded the information in an Amazon bucket created for this project.<br/>
A connection was stablished with the AWS database to Postgres.<br/>
Finally with the help of PySpark we retrieved the dataset from AWS into our Google Colab, cleaned the data and then proceed to store the data in our Postgres tables.

First we filter the data to retrieve all the rows where the total_votes count is equal to or greater than 20 to pick reviews that are more likely to be helpful.

![](resources/images/1.jpg)

From the dataframe filtered previously we will filter again all the rows where the number of helpful_votes divided by total_votes is equal to or greater than 50%.

![](resources/images/2.jpg)

Then we use the previous dataframe we create a new dataframe to retrieve all the rows where a review was written as part of the Vine program (paid).

![](resources/images/3.jpg)

We repeat the previous step but this time retrieve all the rows where the review was not part of the Vine program (unpaid).

![](resources/images/4.jpg)


## Results

From the previous steps performed we proceed to answer the following questions.

* How many Vine reviews and non-Vine reviews were there?

![](resources/images/reviews-count.jpg)

* How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?

![](resources/images/five-stars-review.jpg)

* What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

![](resources/images/percentages.jpg)

## Summary 

From the previous analysis we can see that the percentage of 5-stars reviews paid is 25% and the percentage of 5-stars reviews unpaid is almost 50%, therefore we could say that the unpaid reviewers are more likely to like the products than the paid reviewers.<br/>
To support this statement and since the population of the paid reviewers is so small, we could perform a t-test to compare the two populations (paid or unpaid) and see if they are statistically equal and, with this we could see if it's worth the cost to pay 4 reviewers or to pay more reviewers or to not pay them and only keep the unpaid reviewers.


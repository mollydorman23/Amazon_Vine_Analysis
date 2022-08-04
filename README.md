# Amazon_Vine_Analysis

## Analysis Overview

The purpose of this project is to analyze Amazon reviews written by members of the paid Amazon Vine program. The Amazon Vine program is a service that allows manufacturers and publishers to receive reviews for their products. Companies pay a small fee to Amazon and provide products to Amazon Vine members, who are then required to publish a review.

To begin, we were given a selection of approximately 50 Amazon review datasets listed at the following web address: https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt. Each dataset contains reviews of a specific product, from clothing apparel to wireless products. 

I selected one datasets and used PySpark to perform the ETL process to extract the dataset, transform the data, connect to an AWS RDS instance, and load the transformed data into pgAdmin. Next, I used PySpark to determine if there is any bias toward favorable reviews from Vine members in the dataset I chose: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Grocery_v1_00.tsv.gz

Below, you can review the results from the analysis I performed around reviews for Amazon grocery products. 

- - - - 

## Results

* How many Vine reviews and non-Vine reviews were there?

There are 61 paid reviews (Vine) and 28287 unpaid reviews (non-vine) when you filter out reviews with 20+ votes (which we labeled as “helpful_votes”) and then we executed a filter to ensure that the number of helpful_votes divided by total_votes is greater than or equal to 50%.

![total paid reviews](https://user-images.githubusercontent.com/103781847/182910716-06226a67-592b-4c9f-bea9-116822269be1.png)

![total unpaid reviews](https://user-images.githubusercontent.com/103781847/182910734-08b28e02-0018-4bf2-9256-dbb203384c9f.png)

* How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?

20 of the Vine reviews were 5 stars and 15,689 of the non-Vine reviews were 5 stars.

![5-star paid reviews](https://user-images.githubusercontent.com/103781847/182910789-5c9d9c16-ad81-4168-9f5b-2062e9909a30.png)

![5-star unpaid reviews](https://user-images.githubusercontent.com/103781847/182910817-c3e78417-f111-4622-901c-6d14f1e93ee7.png)

* What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

~32.8% of the Vine reviews were 5 stars and ~55.5% of the non-Vine reviews were 5 stars.

![percent of 5 star paid reviews](https://user-images.githubusercontent.com/103781847/182911123-f4819c10-cbc0-40ec-8936-95c520fddda0.png)

![percent of 5 star unpaid reviews](https://user-images.githubusercontent.com/103781847/182911152-8e557926-f740-4e1b-966a-778e610db939.png)

- - - - 

## Summary: 

I was honestly surprised to see that there is a higher percentage of 5-star reviews for the unpaid review set, than the paid review set. As such, I would not say that there is a positivity bias for Vine reviews, due to the reviewers being paid to leave reviews. As such, I wouldn’t necessarily be paying Amazon for reviews of my grocery products, since the unpaid reviews are just as, if not more helpful!

One additional analysis that we could do with the dataset to support my statement/conclusion above would be to perform a statistical summary of the two datasets and the dataset overall (paid +unpaid) to see if there are any data outliers or a data-configuration structure that points to potentially needing a larger dataset. If so, we could change the way we filtered the data to show more data points and we could also perform the same analysis for other products on the dataset list to see if there is a positivity bias for other types of Amazon products. 

- - - - 

### Products Used:
1. Google Colab
2. Pyspark
3. Postgres/pgAdmin
4. AWS RDS

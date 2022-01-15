# Amazon_Vine_Analysis

## Overview of the analysis: 
The purpose of this analysis is to evaluate if there are any signs of bias in reviews left through the Amazon Vine Program.  According to Amazon (www.amazon.com/vine/about) "_Amazon Vine invites the most trusted reviewers on Amazon to post opinions about new and pre-release items to help their fellow customers make informed purchase decisions. Amazon invites customers to become Vine Voices based on their reviewer rank, which is a reflection of the quality and helpfulness of their reviews as judged by other Amazon customers. Amazon provides Vine members with free products that have been submitted to the program by participating vendors. Vine reviews are the independent opinions of the Vine Voices. The vendor cannot influence, modify or edit the reviews. Amazon does not modify or edit Vine reviews, as long as they comply with our posting guidelines._".  The intent of the program is _"to provide customers with more information including honest and unbiased feedback from some of Amazon's most trusted reviewers"._

Technical skills tested in this challenge involved creation of an AWS relational database, connecting the database to PGAdmin, importing data from S3 into a Google Colab notebook, and performing ETL on the dataset using PySpark. I chose to evaluate the video games dataset on S3 found at (https://s3.amazonaws.com/amazon-reviews-pds/tsv/index.txt)



## Results: 

* How many helpful Vine reviews and non-Vine reviews were there?

To analyze this, I first had to read in the data:

![image](https://user-images.githubusercontent.com/90977689/149632839-71c353f0-40b9-4b7b-aaba-2cb7aef215a2.png)

I then dropped any missing data using .dropna():

![image](https://user-images.githubusercontent.com/90977689/149632866-2f5334b3-26f8-4e8c-a7ca-ccff35ba01af.png)

Then I recreated the vine_df from part one of the challenge and selected the required columns.  I then filtered to return only those with greater than or equal to 20 total_votes):

![image](https://user-images.githubusercontent.com/90977689/149632941-4a1867ed-e9ec-41eb-baf1-9d2b5ebc3852.png)

Helpful reviews were determined by whether a review had >50% of the votes as helpful.  A helpful_reviews_df dataframe was created with the following code:

![image](https://user-images.githubusercontent.com/90977689/149633194-4b2678b8-2f6b-4117-b143-920613b6c009.png)

From here it was just a matter of creating two separate data frames, one containing vine == Y and one containing vine == N.  And this was done with the following code:

![image](https://user-images.githubusercontent.com/90977689/149633238-f4cc7734-2c8c-4bcd-b8d6-7bf75de02759.png)

![image](https://user-images.githubusercontent.com/90977689/149633252-5a263c65-cd3c-4c3e-8bad-a50e2a2fab0d.png)

The total number of helpful reviews was 40,565:

![image](https://user-images.githubusercontent.com/90977689/149633294-66b85df1-87e1-425e-b91f-e6c7c3f74050.png)

The total number of helpful reviews by Vine members was 94:

![image](https://user-images.githubusercontent.com/90977689/149633324-fdfe1d7c-f826-452c-b8f4-18c888d14fdb.png)

The total number of helpful reviews by non-Vine members was 40471:

![image](https://user-images.githubusercontent.com/90977689/149633348-6e4b747e-c6d9-43b2-841e-21783d4c650d.png)


* How many helpful Vine reviews were 5 stars? How many helpful non-Vine reviews were 5 stars?

The number of helpful Vine reviews that were 5 stars was 48:

![image](https://user-images.githubusercontent.com/90977689/149633393-98685156-40a9-400f-9b97-028431de16d6.png)

The number of helpful non-Vine reviews were 15,663:

![image](https://user-images.githubusercontent.com/90977689/149633429-2343c892-2ae6-4079-8a5f-b21ac363128a.png)

* What percentage of helpful Vine reviews were 5 stars? What percentage of helpful non-Vine reviews were 5 stars?
In the video game category and looking at reviews that meet our "helpful" criteria, Vine reviewers provided 5-stars 51% of the time, while non-Vine reviewers provided 5-stars just less than 39% of the time.

![image](https://user-images.githubusercontent.com/90977689/149633464-f6dc5f50-c940-4e57-9c30-8490e1326a70.png)

![image](https://user-images.githubusercontent.com/90977689/149633485-05575463-0e85-45b8-8def-24a02b224806.png)


## Summary: 

Based on this analysis of the video game category, the data shows that Vine reviewers provide 5-star reviews at a higher rate than non-vine reviewers.  However, more analysis would need to be undertaken before one could make a statement about bias in the Vine program.  We would need to perform similar analyses across additional categories, not just a single category.  Additionally we would need to perform statistical analysis to understand if the differences we see are statistically significant given the sample size.

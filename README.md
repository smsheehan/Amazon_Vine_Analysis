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


How many Vine reviews were 5 stars? How many non-Vine reviews were 5 stars?
What percentage of Vine reviews were 5 stars? What percentage of non-Vine reviews were 5 stars?

## Summary: 
In your summary, state if there is any positivity bias for reviews in the Vine program. Use the results of your analysis to support your statement. Then, provide one additional analysis that you could do with the dataset to support your statement.

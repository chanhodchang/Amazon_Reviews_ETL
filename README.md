# Amazon_Reviews_ETL
Using PySpark to ETL tsv files from an AWS database and analyze it in PostgreSQL.

## Project Overview
Looked over two tsv files from the AWS Amazon Reviews database and used the ETL process through PySpark to transfer it onto an AWS server in PostgreSQL. From there the data was analyzed especially the data for vine reviews.

## Resources
- Data Source: https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_Mobile_Electronics_v1_00.tsv.gz, https://s3.amazonaws.com/amazon-reviews-pds/tsv/amazon_reviews_us_PC_v1_00.tsv.gz
- Software: Google Colab, Apache PySpark 2.3.3, Amazon Web Services, PostgreSQL 12.2, PgAdmin 4 v4.19

## Summary 
PySpark was used to extract, transform, and load the two Amazon Reviews Datasources to be analyzed on PostgreSQL

1. Imported PySpark on to my Google Colab work environment.
2. Extracted the different tsv files onto the work environment.
3. Set the different StructField for each column, changing it to either StringType, IntegerType, or DateType.
4. Separated the columns and created four different DataFrames.
5. Created separate DataFrames from the vine_table.
6. Analyzed the vine_table DataFrames in PySpark.
7. Loaded the four DataFrames onto PostgreSQL.

## Analysis
- The analysis was taken from the vine_table and displayed the differences in reviews between Vine and Non-Vine Amazon reviewers.
- Amazon Vine was first launched in 2007 and was a service for major companies to pay Amazon to review their products from Vine Reviewers. 
- For the PC Reviews there are 6,871,915 Non-Vine reviews while 36,230 Vine reviews.
While for the Mobile Electronics Reviews there are 104,954 Non-Vine Reviews and 18 Vine Reviews.

- Non-Vine PC Reviews

+-----------+-------------+-----------+
|star_rating|helpful_votes|total_votes|
+-----------+-------------+-----------+
|          5|        47524|      48362|
|          5|        31924|      32373|
|          4|        31417|      32166|
|          4|        28611|      29433|
|          1|        24714|      26143|
+-----------+-------------+-----------+

- Vine PC Reviews

+-----------+-------------+-----------+
|star_rating|helpful_votes|total_votes|
+-----------+-------------+-----------+
|          5|         3028|       3159|
|          5|         2482|       2598|
|          5|         1842|       1907|
|          5|         1661|       1714|
|          4|         1635|       1670|
+-----------+-------------+-----------+

- Non-Vine Mobile Electronics Reviews

+-----------+-------------+-----------+
|star_rating|helpful_votes|total_votes|
+-----------+-------------+-----------+
|          5|          769|        791|
|          3|          435|        448|
|          5|          425|        429|
|          1|          415|        427|
|          1|          323|        337|
+-----------+-------------+-----------+

- Vine Mobile Electronics Reviews

+-----------+-------------+-----------+
|star_rating|helpful_votes|total_votes|
+-----------+-------------+-----------+
|          3|          396|        445|
|          5|          242|        281|
|          4|           42|         55|
|          4|           31|         41|
|          4|           11|         14|
+-----------+-------------+-----------+

- In the analysis there are much more helpful and total votes for Non-Vine Reviewers compared to Vine Reviewers. This might be because there are more Non-Vine Reviewers compared to Vine Reviewers. 
- It seems that the Non-Vine reviews are much more important to the customers as they see it is much more helpful compared to Vine reviews.

- Avg Votes per Star Ratings (Non-Vine PC Reviews)

+-----------+------------------+------------------+
|star_rating|avg(helpful_votes)|  avg(total_votes)|
+-----------+------------------+------------------+
|          5|1.2084664835461658|1.4218291630927042|
|          4|1.5202392350296317|1.8044057126928916|
|          3|1.8001080826144202|2.5380843830447857|
|          2|1.6481129197748259|2.6600232938631763|
|          1| 2.438265712223101| 4.182918122175476|
+-----------+------------------+------------------+

- Avg Votes per Star Ratings (Vine PC Reviews)

+-----------+------------------+------------------+
|star_rating|avg(helpful_votes)|  avg(total_votes)|
+-----------+------------------+------------------+
|          5|  5.90201196994779| 6.886667515599134|
|          4| 5.082655826558265| 5.957844022884673|
|          3| 5.661013485901103| 7.069064160196159|
|          2| 4.017083587553386|5.5070164734594265|
|          1|6.7227722772277225| 9.168316831683168|
+-----------+------------------+------------------+

- Avg Votes per Star Ratings (Non-Vine Mobile Electronics Reviews)

+-----------+------------------+------------------+
|star_rating|avg(helpful_votes)|  avg(total_votes)|
+-----------+------------------+------------------+
|          5| 1.180909908702892|1.4250770379160527|
|          4|1.2654573609114037|1.4955757106514767|
|          3|1.1515930113052415| 1.532168550873587|
|          2| 1.169380216171843|1.7451087700095773|
|          1|1.4519504151029228|2.2470146707608323|
+-----------+------------------+------------------+

- Avg Votes per Star Ratings (Vine Mobile Electronics Reviews)

+-----------+------------------+------------------+
|star_rating|avg(helpful_votes)|  avg(total_votes)|
+-----------+------------------+------------------+
|          5|              43.5|52.166666666666664|
|          4|              15.0|20.166666666666668|
|          3|             99.75|            116.25|
|          2|               2.0|               5.0|
+-----------+------------------+------------------+

- There are an average of more votes for Vine Reviews compared to Non-Vine Reviews.
- It also shows that there are more votes for the 5 star on Vine reviews compared to Non-Vine Reviews.

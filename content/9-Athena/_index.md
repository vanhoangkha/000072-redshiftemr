---
title : "Analysis with Athena"
date: 2024-01-01
weight : 9
chapter : false
pre : " <b> 9. </b> "
---


#### Analysis with Athena
So far, we have stored several datasets in Amazon S3 and indexed them in the AWS Glue data catalog. With Amazon Athena, we will be able to explore data using standard SQL queries.

Explore transformed data using Athena
1. In this step, we will analyze the converted data using Amazon Athena.
- Sign in to the Amazon Athena Console.
- If you see a message asking you to create an S3 bucket first to store the results of your queries, follow these steps:
- Go to the S3 dashboard and create a bucket using your preferred name, e.g. yourname-query-results
- After creating the bucket, go back to the Athena dashboard and Select 'Settings' in the upper right corner of the panel.
Enter the bucket name you just created, making sure you include a trailing slash: s3://yourname-query-results/
- Click Save
- Because Athena uses AWS Glue collections to track data sources, any S3-based tables in Glue are visible to Athena.
- On the left panel, select 'analyticsworkshopdb' from the drop-down list
- Run the following query:

```
SELECT artist_name,
       count(artist_name) AS count
FROM processed_data
GROUP BY artist_name
ORDER BY count desc

```

![Data Analytics on AWS](/images/9/0001.png?featherlight=false&width=90pc)

2. Explore the Athena interface and try running some queries. Try querying the emr_processed_data table.
This query returns a list of tracks played back repeatedly by devices. Later, we will express this query using QuickSight.

```
SELECT device_id,
       track_name,
       count(track_name) AS count
FROM processed_data
GROUP BY device_id, track_name
ORDER BY count desc

```

![Data Analytics on AWS](/images/9/0002.png?featherlight=false&width=90pc)

You can run similar Athena queries and explore the data further.

In the Next module, we will perform real-time analytics using Amazon Kinesis Data Analytics.
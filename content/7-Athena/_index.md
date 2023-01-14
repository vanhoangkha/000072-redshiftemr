+++
title = "Analysis with Athena"
date = 2021
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

---

Next, we saved some data sets in Amazon S3, and cataloged them in the AWS Glue Data Catalog. With Amazon Athena we will be able to explore data using basic SQL queries

![Data Analysis on AWS](/images/7/athena.png?featherlight=false&width=60pc)



#### Explore transformed data with Athena

In this step we will analyze the converted data using Amazon Athena

1. Go to [Amazon Athena service admin interface](https://console.aws.amazon.com/athena/home?region=ap-southeast-1#query)

{{%notice tip%}}
If you see a message asking you to first create an S3 bucket to store query results, follow these steps. \
\
Go to **admin interface of S3 service** and create a bucket using a name like **yourname-query-results**. \
After creating the bucket, go back to the Athena console and click **Settings** in the right corner of the console. \
Enter the name of the bucket you just created, and make sure it includes a slash: **s3://yourname-query-results/**. \
Click **Save**.
{{%/notice%}}

2. Athena uses the AWS Glue catalog to keep track of the data source, any S3 tables supported in Glue will show up in Athena.
  + On the left, select **analyticsworkshopdb**.
  Run the query command:

```
SELECT artist_name,
       count(artist_name) AS count
FROM processed_data
GROUP BY artist_name
ORDER BY count desc
```

![Data Analysis on AWS](/images/7/1.png?featherlight=false&width=90pc)

3. Explore Athena's interface and try running some queries. Try query table ```emr_processed_data```.

![Data Analysis on AWS](/images/7/2.png?featherlight=false&width=90pc)

4. This query will return a list of tracks played multiple times by devices. Next, we will visualize this query using QuickSight:

```
SELECT device_id,
       track_name,
       count(track_name) AS count
FROM processed_data
GROUP BY device_id, track_name
ORDER BY count desc
```
![Data Analysis on AWS](/images/7/3.png?featherlight=false&width=90pc)

---

You can run familiar Athena queries and explore more data.
In the next section, we'll use Athena again to build dashboards and visualize data on Amazon QuickSight.
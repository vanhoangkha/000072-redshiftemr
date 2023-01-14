+++
title = "Query data with Athena"
date = 2020
weight = 4
chapter = false
pre = "<b>2.4 </b>"
+++


#### Query data using Amazon Athena

We will now query the cataloged simulated data using Amazon Athena.

1. Go to [Athena service admin interface](https://console.aws.amazon.com/athena/home?region=ap-southeast-1#query)

![Data Analysis on AWS](/images/2/00020.png?featherlight=false&width=90pc)

2. Select **Manage**

![Data Analysis on AWS](/images/2/00021.png?featherlight=false&width=90pc)

3. Select **Location of query result**. Select **Save**

![Data Analysis on AWS](/images/2/00022.png?featherlight=false&width=90pc)

4. In the left drop-down table (**Database**), select **analyticsworkshopdb** > select table **raw**.
  + Click on **3 dots** (3 vertical dots) > select **Preview Table**.
  + See the output section.
  + In the query editor, paste the query text below and Click **Run Query**.

```
SELECT activity_type,
         count(activity_type)
FROM raw
GROUP BY activity_type
ORDER BY activity_type
```

![Data Analysis on AWS](/images/2/00023.png?featherlight=false&width=90pc)

Congratulations on completing the data catalog step, continue with the next step of data migration using AWS Glue ETL.
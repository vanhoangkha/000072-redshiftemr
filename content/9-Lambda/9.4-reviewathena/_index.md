+++
title = "Testing data with Athena"
date = 2021
weight = 4
chapter = false
pre = "<b>9.4 </b>"
+++

#### Confirmed via Athena

Now we will confirm the result via Athena

1. Go to [Athena service interface](https://console.aws.amazon.com/athena/home?region=ap-southeast-1#query).
  + In the left pane, select **analyticsworkshopdb** from the drop-down.
  Run the following query command:

```
SELECT track_name as "Track Name",
    artist_name as "Artist Name",
    count(1) as "Hits"
FROM analyticsworkshopdb.processed_data
GROUP BY 1.2
ORDER BY 3 DESC
LIMIT 5;
```

![Data Analysis on AWS](/images/9/16.png?featherlight=false&width=90pc)

2. Compare the query result with the result from the lambda function, both will give the same result.


Through this section you can now create Lambda functions and perform data queries with Lambda.
In the next part, we will try to build Data Warehouse on Amazon Redshift.
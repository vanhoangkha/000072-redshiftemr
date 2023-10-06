---
title : "Verify newly created tables in catalog"
date : "`r Sys.Date()`"
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

#### Verify newly created tables in catalog

1. Navigate to the Glue Catalog and explore the crawled data:

- Go to: [](https://console.aws.amazon.com/glue/home?region=us-east-1#catalog:tab=databases)
- Select analyticsworkshopdb
- Select Tables in analyticsworkshopdb

![Data Analytics on AWS](/images/4/00021.png?featherlight=false&width=90pc)

2. Select raw

![Data Analytics on AWS](/images/4/00022.png?featherlight=false&width=90pc)

3. Walk around and explore the schema for your dataset looking for averageRecordSize, recordCount, compressionType

![Data Analytics on AWS](/images/4/00023.png?featherlight=false&width=90pc)

4. Query imported data with Amazon Athena

- Query the imported data using Amazon Athena
- Go to: [](https://us-east-1.console.aws.amazon.com/athena/home?region=us-east-1#query)

![Data Analytics on AWS](/images/4/00024.png?featherlight=false&width=90pc)

5. If necessary, select "Edit seetings" in the green warning near the top of the Athena console.
Query result location: Under "Under Query result", select s3://yourname-analytics-workshop-bucket/query_results/
Select "Save".


![Data Analytics on AWS](/images/4/00025.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/4/00026.png?featherlight=false&width=90pc)


6. Select the "Editor tab" tab.
On the left panel (Database), select analyticsworkshopdb > select the "raw" table.
Select 3 dots (3 vertical dots) > Select "Preview Table".
Review the returned results.


![Data Analytics on AWS](/images/4/00027.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/4/00028.png?featherlight=false&width=90pc)

7. In the query editor, paste the following query:

```
SELECT activity_type,
         count(activity_type)
FROM raw
GROUP BY activity_type
ORDER BY activity_type
```


![Data Analytics on AWS](/images/4/00029.png?featherlight=false&width=90pc)
+++
title = "Check Glue catalog"
date = 2020
weight = 3
chapter = false
pre = "<b>2.3 </b>"
+++

#### Confirm the newly created table in the catalog

Navigate to Glue Catalog and explore crawled data

1. Go to [AWS Glue service database admin page](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=databases)
  + Click **analyticsworkshopdb**.
  + Click **Tables in analyticsworkshopdb**.
  + Click **raw**.

![Data Analysis on AWS](/images/2/00018.png?featherlight=false&width=90pc)

2. Check the dataset's schemas.
    + Find the data ```averageRecordSize```, ```recordCount```, ```compressionType```
   
Next we will perform a data query using **Amazon Athena**.

![Data Analysis on AWS](/images/2/00019.png?featherlight=false&width=90pc)
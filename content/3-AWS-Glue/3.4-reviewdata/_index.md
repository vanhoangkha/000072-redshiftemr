+++
title = "Data Check"
date = 2020
weight = 4
chapter = false
pre = "<b>3.4 </b>"
+++


#### Confirm - The converted/processed data has gone to S3

After we run the ETL script successfully, we will return to the S3 service interface to check the converted data.

1. Go to [S3 admin interface](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-1)

2. Click - **yourname-analytics-workshop-bucket > data**.
  + Open the **processed-data** folder:
  + Check that files with format **.parquet** have been created in the folder.
  
![Data Analysis on AWS](/images/3/00029.png?featherlight=false&width=90pc)

Congratulations on your successful data migration with AWS Glue, we can query the data using Amazon Athena.
We still have many ways to process data such as using Glue Studio, Glue DataBrew and Amazon EMR.
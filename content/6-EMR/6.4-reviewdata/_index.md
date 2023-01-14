+++
title = "Data Check"
date = 2021
weight = 4
chapter = false
pre = "<b>6.4 </b>"
+++

#### Confirm the converted and processed data to S3

In this step we will check and confirm the EMR transform job created the dataset in the S3 bucket.

Go to [S3 admin interface](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-1)
  + Click **yourname-analytics-workshop-bucket > data**.
  + Open a new folder **emr-processed-data**.
  + Check file format is **.parquet**.


![Data Analysis on AWS](/images/6/14.png?featherlight=false&width=90pc)
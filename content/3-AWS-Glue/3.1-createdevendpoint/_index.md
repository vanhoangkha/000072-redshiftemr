+++
title = "Create Development Endpoint"
date = 2020
weight = 1
chapter = false
pre = "<b>3.1 </b>"
+++

#### Create Glue Development Endpoint

In this step we will create the AWS Glue Dev Endpoint to develop Glue ETL scripts using PySpark.


1. Go to [Glue Development Endpoint admin interface](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=devEndpoints)

+ Click - **Add endpoint**.

![Data Analysis on AWS](/images/3/1.png?featherlight=false&width=90pc)

2. At the **Set up your development endpoint** page.
  + Development endpoint name: ```analyticsworkshopEndpoint1```
  + IAM role **AnalyticsworkshopGlueRole**
  + Expand **Security configuration.. parameters**
    + Data processing units (DPUs): 2 (this will reduce the cost of running the lab)
  + Optional extra Tags:
    + workshop: AnalyticsOnAWS
  + Click **Next**

![Data Analysis on AWS](/images/3/2.png?featherlight=false&width=90pc)

3. At the **Networking** page.
    + Click **Skip networking information**.
    + Click **Next**.

![Data Analysis on AWS](/images/3/3.png?featherlight=false&width=90pc)

4. At the **SSH public key** page.
  + Leave default configuration.
  + Click **Next**.

![Data Analysis on AWS](/images/3/5.png?featherlight=false&width=90pc)

5. At **Reviews** page.
  + Check the configuration again.
  + Click **Finish**

![Data Analysis on AWS](/images/3/6.png?featherlight=false&width=90pc)

6. This will take a few minutes (6 - 10 minutes) to create a new Glue Development Endpoint.

![Data Analysis on AWS](/images/3/7.png?featherlight=false&width=90pc)

7. You will see the status change from PROVISIONING to READY

![Data Analysis on AWS](/images/3/8.png?featherlight=false&width=90pc)

You must wait for this step to succeed before moving on to the next step
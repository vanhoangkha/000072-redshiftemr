+++
title = "Create IAM Role"
date = 2021
weight = 1
chapter = false
pre = "<b>2.1 </b>"
+++

#### Create IAM Role

In this step, we will go to the IAM Console and create a new service role for AWS Glue. This will make it possible for AWS Glue to access the data stored in S3 and be able to create the necessary entities in the Glue Data Catalog.

1. Go to admin interface [IAM Roles](https://console.aws.amazon.com/iam/home?region=ap-southeast-1#/roles)
+ Click **Create role**.
  + Select the service that will use the role: **Glue**.
  + Click **Next: Permissions**.

![Data Analysis on AWS](/images/2/1.png?featherlight=false&width=90pc)

2. Role name: **AnalyticsworkshopGlueRole**.

![Data Analysis on AWS](/images/2/2.png?featherlight=false&width=90pc)

3. Do a policy search **AmazonS3FullAccess**.
   - Click the policy **AmazonS3FullAccess**.
   - Do a policy search **AWSGlueServiceRole**.
   - Click the policy **AWSGlueServiceRole**.
   - At the **Add tags** page.
   - Add tags Key = **workshop** and Value = **AnalyticsOnAWS**.
   - Click **Create role**

![Data Analysis on AWS](/images/2/3.png?featherlight=false&width=90pc)

4. Complete role creation.

![Data Analysis on AWS](/images/2/3.1.png?featherlight=false&width=90pc)
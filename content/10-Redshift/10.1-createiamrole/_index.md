+++
title = "Create Redshift IAM role"
date = 2021
weight = 1
chapter = false
pre = "<b>10.1 </b>"
+++

#### Create Redshift IAM role

In this step we will create IAM role for Redshift cluster

1. Go to [IAM console](https://console.aws.amazon.com/iam/home?region=ap-southeast-1#/roles).
  + Click **Create role**.


![Data Analysis on AWS](/images/10/1.png?featherlight=false&width=90pc)

2. Select **Redshift**.
  + Select **Redshift - customizable** under **Select your use case**.

![Data Analysis on AWS](/images/10/2.png?featherlight=false&width=90pc)

3. Click **Next**.


![Data Analysis on AWS](/images/10/3.png?featherlight=false&width=90pc)

4. Let **Role Name** be ```Analyticsworkshop_RedshiftRole```.


![Data Analysis on AWS](/images/10/4.png?featherlight=false&width=90pc)

5. Check the following policies:
    + **AmazonS3FullAccess**.a
    + **AWSGlueConsoleFullAccess**.
    + Optional extra Tags:
      + workshop: AnalyticsOnAWS.
    + Click **Create role**.

![Data Analysis on AWS](/images/10/5.png?featherlight=false&width=90pc)

6. Create a successful role.

![Data Analysis on AWS](/images/10/6.png?featherlight=false&width=90pc)

Next we will proceed to create a Redshift cluster.
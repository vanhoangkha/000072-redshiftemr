---
title : "Create IAM Role"
date: 2024-01-01
weight : 1
chapter : false
pre : " <b> 4.1 </b> "
---

#### Create IAM Role

In this step, we will access the IAM Console and create a new AWS Glue service role. This allows AWS Glue to access the data stored in S3 and create the required entities in the Glue Data Collection.

1. Go to:
- Select Create role
- Select the service that will use this role: Glue
- Select Next

![Data Analytics on AWS](/images/4/0001.png?featherlight=false&width=90pc)

2. Search AmazonS3FullAccess
- Select the checkbox of this item
- Search for AWSGlueServiceRole
- Select the checkbox of this item
- Select Next

![Data Analytics on AWS](/images/4/0002.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/4/0003.png?featherlight=false&width=90pc)

3. Role name: AnalyticsworkshopGlueRole
- Make sure that only two policies are attached to this role (AmazonS3FullAccess, AWSGlueServiceRole)
- Option to add Tag, for example: workshop: AnalyticsOnAWS
- Select Create role

![Data Analytics on AWS](/images/4/0004.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/4/0005.png?featherlight=false&width=90pc)

4. Create a successful role.

![Data Analytics on AWS](/images/4/0006.png?featherlight=false&width=90pc)
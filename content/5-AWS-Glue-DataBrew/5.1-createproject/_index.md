+++
title = "Create DataBrew project"
date = 2021
weight = 1
chapter = false
pre = "<b>5.1 </b>"
+++


#### Create DataBrew project

1. Go to [Glue DataBrew admin interface](https://console.aws.amazon.com/databrew/home?region=ap-southeast-1#landing)
  + Click - **Create project**

![Data Analysis on AWS](/images/5/1.png?featherlight=false&width=90pc)

2. Enter **Project name: AnalyticsOnAWS-GlueDataBrew** as shown below.
  + Under **Select a dataset** select **New dataset**.
  + In the **New dataset details** field, enter **raw-dataset** as shown below.

![Data Analysis on AWS](/images/5/2.png?featherlight=false&width=90pc)

3. Under **Connect to new dataset**.
  + Select **All AWS Glue tables** , you will see all the databases in the AWS Glue Catalog shown below.

![Data Analysis on AWS](/images/5/3.png?featherlight=false&width=90pc)

4. Click **analyticsworkshopdb**.
  + Select table **raw**.

![Data Analysis on AWS](/images/5/4.png?featherlight=false&width=90pc)

5. Under **Permissions**.
  + Select **Role name** as **Create new IAM role**.
  + Enter **AnalyticsOnAWS-GlueDataBrew** in **New IAM role suffix**.

![Data Analysis on AWS](/images/5/5.png?featherlight=false&width=90pc)

6. When the Glue DataBrew project is successfully created, you will see the screen below.

![Data Analysis on AWS](/images/5/6.png?featherlight=false&width=90pc)
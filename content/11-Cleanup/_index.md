+++
title = "Clean up resources"
date = 2020
weight = 11
chapter = false
pre = "<b>11. </b>"
+++

---

If you don't clean up all your resources, you will continue to be charged for using AWS

Make sure you delete all the resources you create through the steps below, and only delete the resources used in the workshop.

---

#### Resources to be deleted.

+ Kinesis Firehose Delivery Stream

  + Go To: Kinesis Console [Click here](https://console.aws.amazon.com/firehose/home?region=ap-southeast-1#/)
  + Remove Firehose: **analytics-workshop-stream**

+ Lambda

  + Go To: Lambda Console [Click here](https://console.aws.amazon.com/lambda/home?region=ap-southeast-1)
  + Go to function list and select **Analyticsworkshop_top5Songs**.
  + Under the **Actions** drop-down list, select **Delete**.

+ Glue Database

  + Go To: Glue Console [Click here](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=databases)
  + Delete Database: **analyticsworkshopdb**

+ Glue Crawler

  + Go To: Glue Crawlers [Click here](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=crawlers)
  + Xpas Crawler: **AnalyticsworkshopCrawler**

+ Glue Dev Endpoints

  + Go To: Glue Dev Endpoints [Click here](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=devEndpoints)
  + Delete endpoint: **analyticsworkshopEndpoint1**
  + Xpas endpoint: **analyticsworkshopEndpoint2**

+ Glue Studio Job

  + Go To: https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=jobs
  + Select **AnalyticsOnAWS-GlueStudio**
  + Press **Action** and select **Delete**

+ Glue DataBrew projects

  + Go To: https://console.aws.amazon.com/databrew/home?region=ap-southeast-1#projects
  + Select **AnalyticsOnAWS-GlueDataBrew**
  + Press **Action** and select **Delete**
  + Select **Delete attached receipe** and press **Delete**

+ Glue DataBrew datasets

  + Go to: https://console.aws.amazon.com/databrew/home?region=ap-southeast-1#datasets
  + Select dataset: **reference-data-dataset** and **raw-dataset**
  + Press **Action** and select **Delete**
  + Confirm deletion by pressing **Delete**

+ Glue DataBrew Jobs

  + Go To: https://console.aws.amazon.com/databrew/home?region=ap-southeast-1#jobs?tab=profile
  + Select dataset: **raw-dataset profile job**
  + Press **Action** and select **Delete**
  + Confirm deletion by pressing **Delete**

+ Sagemaker Notebook

  + You can delete downloaded notebook files throughout the lab
  + Go to: Notebooks Console [Click here](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=notebooks)
  + Stop and then delete Notebook: **aws-glue-AnalyticsworkshopRedshiftNotebook**
  + Stop and then delete Notebook: **aws-glue-AnalyticsworkshopNotebook**

+ Delete Glue connection

  + Go to: Glue Connections [Click here](https://ap-southeast-1.console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=connections)
  + select **analytics_workshop**
  + From **Actions** select **Delete Connection**
  + Click **Delete**

+ Delete IAM Role

  + Go To: IAM Console [Click here](https://console.aws.amazon.com/iam/home?region=ap-southeast-1#/roles)
  + Find AnalyticsworkshopGlueRole
  + Delete Role: **AnalyticsworkshopGlueRole**
  + Delete Role: **Analyticsworkshop_RedshiftRole**
  + Find Analyticsworkshop_top5Songs in the search box
  + Select and delete. [**Analyticsworkshop_top5Songs-role-**]

+ Delete Redshift cluster

  + Go To: Redshift Console [Click here](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1)
  + Select **redshift-cluster-1**
  + From **Actions**, select **Delete**
  + Uncheck **Create final snapshot**
  + Click **Delete**

+ Delete S3 Gateway Endpoint

  + Go To: S3 Gateway Endpoints [Click here](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#Endpoints:sort=vpcEndpointId)
  + Select **RedshiftS3EP**
  + From **Actions** select **Delete Endpoint**

+ Revert Security Group rules

  + Go To: EC2 Security Groups [Click here](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#SecurityGroups:sort=tag:Name)
  + With ```default``` security group:
    + Click Inbound Rules
      + Click Edit Rules
      + Delete used with S3 prefix list ID
      + Click Save rules
    + Click Outbound rules
      + Click Edit Rules
      + Delete All TCP rules.
      + Click Save rules

+ Delete S3 bucket

  + Go To: S3 Console [Click here](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-1)
  + Delete Bucket: **yourname-analytics-workshop-bucket**
    + You will need **Empty** bucket first
    + When the bucket is empty, **Delete** bucket

+ Delete the Cognito CloudFormation Stack

  + Go To: CloudFormation [Click here](https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/)
  + Click: **Kinesis-Data-Generator-Cognito-User**
  + Click: **Actions > DeleteStack**
  On the confirmation screen:
    + Press Delete

+ Close QuickSight account

  + Go To: Quicksight Console [Click here](https://ap-southeast-1.quicksight.aws.amazon.com/en/admin#permissions)
  + Click **Unsubscribe**

+ Cognito Userpool

  + Go To: Cognito Console [Click here](https://ap-southeast-1.console.aws.amazon.com/cognito/users/)
  + Click **Kinesis Data-Generator Users**
  + Click **Delete Pool**
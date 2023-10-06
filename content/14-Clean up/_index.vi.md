---
title : "Dọn dẹp tài nguyên"
date :  "`r Sys.Date()`" 
weight : 14
chapter : false
pre : " <b> 14. </b> "
---

#### Dọn dẹp tài nguyên


#### Kinesis Firehose Delivery Stream

- Go to: Kinesis Console 
- Delete Firehose: analytics-workshop-stream

#### Kinesis Data Stream

- Go to: Kinesis Console 
- Delete Data Stream: analytics-workshop-data-stream

#### Kinesis Data Analytics Studio Notebook

- Go to: Kinesis Console 
- Delete Notebook: AnalyticsWorkshop-KDANotebook

#### Lambda

- Go to: Lambda Console

- Navigate to list of functions and select Analyticsworkshop_top5Songs.

- Under Actions drop down menu, select Delete.

#### Glue Database

- Go to: Glue Console
- Delete Database: analyticsworkshopdb

#### Glue Crawler

- Go to: Glue Crawlers 
- Delete Crawler: AnalyticsworkshopCrawler

#### Glue Studio Job

- GoTo: https://us-east-1.console.aws.amazon.com/gluestudio/home?region=us-east-1#/jobs 
- Check AnalyticsOnAWS-GlueStudio
- Check AnalyticsOnAWS-GlueIS
- Check AnalyticsOnAWS-Redshift
- Click Action and choose Delete job(s)

#### Glue DataBrew projects

- GoTo: https://console.aws.amazon.com/databrew/home?region=us-east-1#projects 
- Check AnalyticsOnAWS-GlueDataBrew
- Click Action and choose Delete
- Check Delete attached receipe and click Delete

#### Glue DataBrew datasets

- GoTo: https://console.aws.amazon.com/databrew/home?region=us-east-1#datasets 
- Check dataset name: reference-data-dataset and raw-dataset
- Click Action and choose Delete
- Confirm deletion by clicking Delete

#### Glue DataBrew Jobs

- GoTo: https://console.aws.amazon.com/databrew/home?region=us-east-1#jobs?tab=profile 
- Check dataset name: raw-dataset profile job
Click Action and choose Delete
Confirm deletion by clicking Delete

#### Delete Glue connection

- Go to: Glue Connections 

- Select analytics_workshop

- From Actions select Delete Connection

- Click Delete


#### Delete IAM Role

- Go to: IAM Console 
- Search for following roles and delete:
- Analyticsworkshop-GlueISRole
- Analyticsworkshop_RedshiftRole
- AnalyticsworkshopKinesisAnalyticsRole
- Analyticsworkshop_top5Songs-role-

#### Delete IAM Policy

- Go to: IAM Console 

- Search for following policies and delete:

- AWSGlueInteractiveSessionPassRolePolicy

#### Delete Redshift cluster

- Go to: Redshift Console  
- Select redshift-cluster-1
- From Actions menu, select Delete.
- Uncheck Create final snapshot
- Click Delete

#### Delete S3 Gateway Endpoin

- Go to: S3 Gateway Endpoints  
- Select RedshiftS3EP
- From Actions select Delete Endpoint

#### Revert Security Group rules

- Go to: EC2 Security Groups  
- For the default security group:
- Click on Inbound Rules
- Click Edit Rules
- Delete the row with S3 prefix list ID
- Click Save rules
- Click on Outbound rules
- Click Edit Rules
- Delete the self-referencing All TCP rule.
- Click Save rules

#### Delete S3 bucket

- Go to: S3 Console  
- Delete Bucket: yourname-analytics-workshop-bucket
- You may need to first Empty the bucket as prompted
- Once emptied, proceed to Delete the bucket

#### Delete the Cognito CloudFormation Stack

- Go to: CloudFormation  
- Click: Kinesis-Data-Generator-Cognito-User
- Click: Actions > DeleteStack
- On confirmation screen:
- Click Delete

#### Close QuickSight account

- Go to: Quicksight Console  

- Click: Unsubscribe

####  Cognito Userpool

- Go to: Cognito Console  
- Click Kinesis Data-Generator Users
- Click Delete Pool

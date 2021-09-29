+++
title = "Dọn dẹp"
date = 2020
weight = 11
chapter = false
pre = "<b>11. </b>"
+++

---

Nếu không dọn dẹp tất cả tài nguyên bạn sẽ tiếp tục bị charge phí sử dụng AWS

Hãy chắc rằng bạn xoá tát cả tài nguyên bạn tạo qua các bước dưới đây

---

#### Các tài nguyên để xoá

+ Kinesis Firehose Delivery Stream

  + Đi Đến: Kinesis Console [Nhấn vào đây](https://console.aws.amazon.com/firehose/home?region=ap-southeast-1#/)
  + Xoá Firehose: **analytics-workshop-stream**

+ Lambda

  + Đi Đến: Lambda Console [Nhấn vào đây](https://console.aws.amazon.com/lambda/home?region=ap-southeast-1)
  + Đi đến list function và chọn **Analyticsworkshop_top5Songs**.
  + Dưới bảng sổ xuống **Actions**, chọn **Delete**.

+ Glue Database

  + Đi Đến: Glue Console [Nhấn vào đây](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=databases)
  + Xoá Database: **analyticsworkshopdb**

+ Glue Crawler

  + Đi Đến: Glue Crawlers [Nhấn vào đây](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=crawlers)
  + Xpas Crawler: **AnalyticsworkshopCrawler**

+ Glue Dev Endpoints

  + Đi Đến: Glue Dev Endpoints [Nhấn vào đây](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=devEndpoints)
  + Xoá endpoint: **analyticsworkshopEndpoint1**
  + Xpas endpoint: **analyticsworkshopEndpoint2**

+ Glue Studio Job

  + Đi Đến: https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=jobs
  + Chọn **AnalyticsOnAWS-GlueStudio**
  + Nhấn **Action** và chọn **Delete**

+ Glue DataBrew projects

  + Đi Đến: https://console.aws.amazon.com/databrew/home?region=ap-southeast-1#projects
  + Chọn **AnalyticsOnAWS-GlueDataBrew**
  + Nhấn **Action** và chọn **Delete**
  + Chọn **Delete attached receipe** và nhấn **Delete**

+ Glue DataBrew datasets

  + Đi đến: https://console.aws.amazon.com/databrew/home?region=ap-southeast-1#datasets
  + Chọn dataset: **reference-data-dataset** and **raw-dataset**
  + Nhấn **Action** và chọn **Delete**
  + Xác nhận xoá bằng cách nhấn **Delete**

+ Glue DataBrew Jobs

  + Đi Đến: https://console.aws.amazon.com/databrew/home?region=ap-southeast-1#jobs?tab=profile
  + Chọn dataset: **raw-dataset profile job**
  + Nhấn **Action** và chọn **Delete**
  + Xác nhận xoá bằng cách nhấn **Delete**

+ Sagemaker Notebook

  + Bạn có thể xoá các file notebook đã tải xuống thông suốt bài lab
  + Đi đến: Notebooks Console [Nhấn vào đây](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=notebooks)
  + Dừng và sau đó xoá Notebook: **aws-glue-AnalyticsworkshopRedshiftNotebook**
  + Dừng và sau đó xoá Notebook: **aws-glue-AnalyticsworkshopNotebook**

+ Delete Glue connection

  + Đi đến: Glue Connections [Nhấn vào đây](https://ap-southeast-1.console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=connections)
  + chọn **analytics_workshop**
  + Từ **Actions** chọn **Delete Connection**
  + Nhấn **Delete**

+ Delete IAM Role

  + Đi Đến: IAM Console [Nhấn vào đây](https://console.aws.amazon.com/iam/home?region=ap-southeast-1#/roles)
  + Tìm AnalyticsworkshopGlueRole
  + Xoá Role: **AnalyticsworkshopGlueRole**
  + Xoá Role: **Analyticsworkshop_RedshiftRole**
  + Tìm Analyticsworkshop_top5Songs trong khung tìm kiếm
  + Chọn và xoá. [**Analyticsworkshop_top5Songs-role-**]

+ Delete Redshift cluster

  + Đi Đến: Redshift Console [Nhấn vào đây](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1)
  + Chọn **redshift-cluster-1**
  + Từ **Actions**, chọn **Delete**
  + Bỏ chọn **Create final snapshot**
  + Nhấn **Delete**

+ Delete S3 Gateway Endpoint

  + Đi Đến: S3 Gateway Endpoints [Nhấn vào đây](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#Endpoints:sort=vpcEndpointId)
  + Chọn **RedshiftS3EP**
  + Từ **Actions** chọn **Delete Endpoint**

+ Revert Security Group rules

  + Đi Đến: EC2 Security Groups [Nhấn vào đây](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#SecurityGroups:sort=tag:Name)
  + Với ```default``` security group:
    + Nhấn Inbound Rules
      + Nhấn Edit Rules
      + Xoá dùng với S3 prefix list ID
      + Nhấn Save rules
    + Nhấn Outbound rules
      + Nhấn Edit Rules
      + Xoá All TCP rule.
      + Nhấn Save rules

+ Delete S3 bucket

  + Đi Đến: S3 Console [Nhấn vào đây](https://s3.console.aws.amazon.com/s3/home?region=ap-southeast-1)
  + Xoá Bucket: **yourname-analytics-workshop-bucket**
    + Bạn sẽ cần **Empty** bucket trước
    + Khi bucket đã rỗng, **Delete** bucket

+ Delete the Cognito CloudFormation Stack

  + Đi Đến: CloudFormation [Nhấn vào đây](https://ap-southeast-1.console.aws.amazon.com/cloudformation/home?region=ap-southeast-1#/stacks/)
  + Nhấn: **Kinesis-Data-Generator-Cognito-User**
  + Nhấn: **Actions > DeleteStack**
  + Ở màn hình confirm:
    + Nhấn Delete

+ Close QuickSight account

  + Đi Đến: Quicksight Console [Nhấn vào đây](https://ap-southeast-1.quicksight.aws.amazon.com/en/admin#permissions)
  + Nhấn **Unsubscribe**

+ Cognito Userpool

  + Đi Đến: Cognito Console [Nhấn vào đây](https://ap-southeast-1.console.aws.amazon.com/cognito/users/)
  + Nhấn **Kinesis Data-Generator Users**
  + Nhấn **Delete Pool**

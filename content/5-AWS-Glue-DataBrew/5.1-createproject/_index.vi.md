+++
title = "Tạo DataBrew project"
date = 2021
weight = 1
chapter = false
pre = "<b>5.1 </b>"
+++


#### Tạo DataBrew project

1. Truy cập đến [giao diện quản trị của Glue DataBrew](https://console.aws.amazon.com/databrew/home?region=ap-southeast-1#landing)
  + Click - **Create project**

![Data Analysis on AWS](/images/5/1.png?featherlight=false&width=90pc)

2. Nhập **Project name: AnalyticsOnAWS-GlueDataBrew** như màn hình dưới đây.
  + Dưới mục **Select a dataset** chọn **New dataset**.
  + Trong mục **New dataset details**, nhập **raw-dataset** như màn hình dưới đây.

![Data Analysis on AWS](/images/5/2.png?featherlight=false&width=90pc)

3. Ở dưới **Connect to new dataset**.
  + Chọn **All AWS Glue tables** , bạn sẽ thấy tất cả các database trong AWS Glue Catalog được thể hiện dưới đây.

![Data Analysis on AWS](/images/5/3.png?featherlight=false&width=90pc)

4. Click **analyticsworkshopdb**.
  + Chọn table **raw**.

![Data Analysis on AWS](/images/5/4.png?featherlight=false&width=90pc)

5. Dưới **Permissions**.
  + Chọn **Role name** là **Create new IAM role**.
  + Nhập **AnalyticsOnAWS-GlueDataBrew** trong **New IAM role suffix**.

![Data Analysis on AWS](/images/5/5.png?featherlight=false&width=90pc)

6. Khi Glue DataBrew project được tạo thành công, bạn sẽ thấy như màn hình dưới đây.

![Data Analysis on AWS](/images/5/6.png?featherlight=false&width=90pc)
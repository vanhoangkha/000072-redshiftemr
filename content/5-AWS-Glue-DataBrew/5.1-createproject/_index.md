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

![Architect](/images/5/glue_databrew_1.png?width=90pc)

2. Nhập **Project name: AnalyticsOnAWS-GlueDataBrew** như màn hình dưới đây.
  + Dưới mục **Select a dataset** chọn **New dataset**.
  + Trong mục **New dataset details**, nhập **raw-dataset** như màn hình dưới đây.

![Architect](/images/5/1.png?width=90pc)

3. Ở dưới **Connect to new dataset**.
  + Chọn **All AWS Glue tables** , bạn sẽ thấy tất cả các database trong AWS Glue Catalog được thể hiện dưới đây.

4. Click **analyticsworkshopdb**.
  + Chọn table **raw**.

5. Dưới **Permissions**.
  + Chọn **Role name** là **Create new IAM role**.
  + Nhập **AnalyticsOnAWS-GlueDataBrew** trong **New IAM role suffix**.

![Architect](/images/5/2.png?width=90pc)

6. Khi Glue DataBrew project được tạo thành công, bạn sẽ thấy như màn hình dưới đây.

![Architect](/images/5/3.png?width=90pc)

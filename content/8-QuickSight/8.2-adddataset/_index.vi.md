+++
title = "Thêm Dataset"
date = 2021
weight = 2
chapter = false
pre = "<b>8.2 </b>"
+++


#### Thêm Dataset 

1. Truy cập đến [giao diện dịch vụ Quick Sight](https://ap-southeast-1.quicksight.aws.amazon.com/en/start).
  + Ở góc trên bên phải, Click **Manage Data**.
  + Click **New Data Set**.

![Architect](/images/8/3.png?width=90pc)

2. Click **Athena**.
  + New Athena data source.
    + Data source name: ```analyticsworkshop```.
    + Click **Validate connection**.
      + Việc này sẽ kiểm tra xem QuickSight có thể truy cập Athena không.
    + Click **Create data source**.

![Architect](/images/8/4.png?width=90pc)

3. Chọn table của bạn:
    + Database: chọn **analyticsworkshopdb**.
    + Tables: chọn **processed_data**.
    + Click **Select**.

![Architect](/images/8/5.png?width=90pc)

4. Hoàn tất tạo data set:
    + Chọn **Directly query your data**.
    + Click **Visualize**.

![Architect](/images/8/6.png?width=90pc)

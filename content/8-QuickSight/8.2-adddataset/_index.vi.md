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

![Data Analysis on AWS](/images/7/4.png?featherlight=false&width=90pc)

2. Click **Athena**.

![Data Analysis on AWS](/images/7/5.png?featherlight=false&width=90pc)


3. New Athena data source.
    + Data source name: ```analyticsworkshop```.
    + Click **Validate connection**.
      + Việc này sẽ kiểm tra xem QuickSight có thể truy cập Athena không.
    + Click **Create data source**.

![Data Analysis on AWS](/images/7/6.png?featherlight=false&width=90pc)

4. Chọn table của bạn:
    + Database: chọn **analyticsworkshopdb**.
    + Tables: chọn **processed_data**.
    + Click **Select**.
![Data Analysis on AWS](/images/7/7.png?featherlight=false&width=90pc)


5. Hoàn tất tạo data set:
    + Chọn **Directly query your data**.
    + Click **Visualize**.


![Data Analysis on AWS](/images/7/8.png?featherlight=false&width=90pc)



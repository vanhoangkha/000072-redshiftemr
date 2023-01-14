+++
title = "Tạo EMR Cluster"
date = 2021
weight = 2
chapter = false
pre = "<b>6.2 </b>"
+++

#### Tạo EMR Cluster và chạy script đã upload lên S3

Ở bước này, chúng ta sẽ tạo EMR cluster và thêm các bước của Spark

1. Truy cập đến [giao diện quản trị của EMR](https://console.aws.amazon.com/elasticmapreduce/home?region=ap-southeast-1#).

  + Click **Create cluster**.

![Data Analysis on AWS](/images/6/7.png?featherlight=false&width=90pc)

2. Tiếp tục với **Create cluster - Quick options**.
  + Đặt tên cho cluster: ```analytics-workshop-transformer```.
  + Chọn tuỳ chọn **Logging** và cung cấp S3 folder:
    + ```s3://yourname-analytics-workshop-bucket/logs/```.
  + Đổi **Launch mode** thành **Step execution**.
  + Ở dưới **Add steps** chọn **Spark application**.

![Data Analysis on AWS](/images/6/8.png?featherlight=false&width=90pc)

3. Click **Configure**.
    + Ở cửa sổ hiện lên, để trống **Spark-submit options**.
    + Cho phần **Application location**, chọn nơi chứa script vừa upload - ```s3://yourname-analytics-workshop-bucket/scripts/emr_pyspark.py```.
    + Click **Select**.
    + Dưới **Arguments**, nhập tên s3 bucket ```yourname-analytics-workshop-bucket```.
    + Cho phần **Action on failure**, chọn **Terminate cluster** .
    + Click **Add** để hoàn thành.

![Data Analysis on AWS](/images/6/9.png?featherlight=false&width=90pc)

4. Tại mục **Software configuration**.
  + Không check tuỳ chọn Use **AWS Glue Data Catalog for table metadata**.
  + Release: **emr-x.x**.
  + Applications: Hadoop x.x.x, Spark x.x.x.
  + Version sẽ được để mặc định là mới nhất.

![Data Analysis on AWS](/images/6/10.png?featherlight=false&width=90pc)

5. Tại mục **Hardware configuration**.
  + Instance type: **m5.xlarge**.
  + Number of Instances: 3 (1 master and 2 core nodes).
  + Để **Security and access** mặc định.

![Data Analysis on AWS](/images/6/10.png?featherlight=false&width=90pc)

  + Click **Create cluster**.


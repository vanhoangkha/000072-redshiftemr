+++
title = "Tạo schema và tables"
date = 2021
weight = 6
chapter = false
pre = "<b>10.6 </b>"
+++

#### Tạo schema và Redshift tables

1. Truy cập đến [giao diện Query Editor của  dịch vụ Redshift](https://us-east-1.console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1#query-editor).
  + Tại trang **Connect to database**.
  + Chọn Redshift cluster chúng ta đã tạo.
  + Chọn Database name là **dev**, và Database user là **admin**.
  + Click **Connect**.


![Data Analysis on AWS](/images/10/32.png?featherlight=false&width=90pc)


2. Chạy các câu query dưới đây để tạo schema.

```
--	Create redshift_lab schema.
CREATE schema redshift_lab;
```


![Data Analysis on AWS](/images/10/33.png?featherlight=false&width=90pc)


1. Chạy các câu query dưới đây để tạo table cho dữ liệu raw và reference.
```
--	Create f_raw_1 table.
CREATE TABLE IF not EXISTS redshift_lab.f_raw_1 (
  uuid			varchar(256),
  device_ts 		timestamp,
  device_id		int,
  device_temp		int,
  track_id		int,
  activity_type		varchar(128),
  load_time		int
);
```

![Data Analysis on AWS](/images/10/34.png?featherlight=false&width=90pc)

```
--	Create d_ref_data_1 table.
CREATE TABLE IF NOT EXISTS redshift_lab.d_ref_data_1 (
  track_id		int,
  track_name	varchar(128),
  artist_name	varchar(128)
);
```
![Data Analysis on AWS](/images/10/35.png?featherlight=false&width=90pc)

Tiếp theo, chúng ta sẽ thực hiện chuyển đổi và load dữ liệu vào Redshift.
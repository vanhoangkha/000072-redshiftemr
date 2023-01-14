+++
title = "Tạo table mới "
date = 2021
weight = 4
chapter = false
pre = "<b>10.9.4 </b>"
+++

#### Tạo table mới và chuyển dữ liệu vào table mới.

1. Dựa trên tất cả các bước tối ưu chúng ta đã đánh giá , chúng ta sẽ tiến hành tạo table mới.
  + Tạo cột mới sử dụng DDL của **f_raw_2** và **d_ref_data_2**

```
--fact table ddl
CREATE TABLE IF NOT EXISTS redshift_lab.f_raw_2 (
  uuid			varchar(40) ENCODE zstd,
  device_ts 		timestamp,
  device_id		int ENCODE az64,
  device_temp		int ENCODE az64,
  track_id		int ENCODE az64,
  activity_type		varchar(16) ENCODE bytedict sortkey,
  load_time		int ENCODE zstd
)
DISTKEY(track_id);
  
--dimension table ddl
CREATE TABLE IF NOT EXISTS redshift_lab.d_ref_data_2 (
  track_id		int,
  track_name		varchar(64),
  artist_name		varchar(64)
)
DISTSTYLE ALL;
```

![Data Analysis on AWS](/images/10/59.png?featherlight=false&width=90pc)

2. Thực hiện câu truy vấn dưới đây để sao chép dữ liệu từ table cũ sang table mới.

```
--copy data from f_raw_1 to f_raw_2
insert into redshift_lab.f_raw_2 select * from redshift_lab.f_raw_1;
  
--copy data from d_ref_data_1 to d_ref_data_2
INSERT into redshift_lab.d_ref_data_2 select * from redshift_lab.d_ref_data_1; 
```

![Data Analysis on AWS](/images/10/60.png?featherlight=false&width=90pc)

Tiếp theo chúng ta sẽ thực hiện thêm bước dọn dẹp và phân tích dữ liệu sau khi chuyển sang table mới.
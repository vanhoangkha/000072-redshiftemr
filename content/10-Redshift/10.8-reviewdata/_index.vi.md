+++
title = "Kiểm tra dữ liệu"
date = 2021
weight = 8
chapter = false
pre = "<b>10.8 </b>"
+++

#### Xác nhận - Chuyển đổi dữ liệu đã đi vào Redshift

1. Sau khi ETL script đã chạy thành công, truy cập đến [giao diện Query Editor của dịch vụ Redshift](https://ap-southeast-1.console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1#query-editor).

  + Chạy câu query dưới đây để kiểm trả số lượng record ở table của dữ liệu raw và reference.

```
select count(1) from redshift_lab.f_raw_1;

select count(1) from redshift_lab.d_ref_data_1;
```

---

![Data Analysis on AWS](/images/10/55.png?featherlight=false&width=90pc)

2. Thử chạy một câu truy vấn phức tạp hơn trên Redshift, ghi chú lại thời gian thực thi nhé.

```
select 
  track_name, 
  artist_name, 
  count(1) frequency
from 
  redshift_lab.f_raw_1 fr
inner join 
  redshift_lab.d_ref_data_1 drf
on 
  fr.track_id = drf.track_id
where 
  activity_type = 'Running'
group by 
  track_name, artist_name
order by 
  frequency desc
limit 10;
```
![Data Analysis on AWS](/images/10/56.png?featherlight=false&width=90pc)


Bạn đã hoàn thành việc load dữ liệu từ S3 vào Redshift sử dụng Glue Serverless ETL. Tiếp theo chúng ta sẽ thực hiện một số bước tối ưu để làm tăng hiệu năng cho câu truy vấn. 

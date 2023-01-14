+++
title = "Query và so sánh hiệu năng"
date = 2021
weight = 6
chapter = false
pre = "<b>10.9.6 </b>"
+++

#### Chạy Query và so sánh hiệu năng

1. Thực hiện câu truy vấn dưới đây, liệt kê danh sách 10 bài nhạc cùng nghệ sĩ biểu diễn cho một loại hoạt động nhất định.

```--Top 10 tracks and corresponding artists for a particular activity type. 
select 
  track_name, 
  artist_name, 
  count(1) frequency
from 
  redshift_lab.f_raw_2 fr
inner join 
  redshift_lab.d_ref_data_2 drf
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

2. Bạn có thể so sánh thời gian thực thi với phần kết quả của bước **10.8** và so sánh tốc độ thực thi.
  + Như trên ảnh dưới, chúng ta có thể thấy thì thời gian thực thi đã giảm từ 12s còn 2s cho câu lệnh query này

![Data Analysis on AWS](/images/10/63.png?featherlight=false&width=90pc)

Chúc mừng bạn đã hoàn tất workshop Phân tích dữ liệu trên AWS.Hi vọng qua workshop này sẽ giúp các bạn làm quen với các dịch vụ và tính năng giúp cho việc xây dựng giải pháp phân tích dữ liệu trên AWS trở nên dễ dàng hơn. 

{{% notice warning %}}
Hãy chắc rằng bạn thực hiện phần dọn dẹp sau khi hoàn thành bài lab, đặc biệt là xóa các Glue dev endpoints và notebooks.
{{% /notice %}}
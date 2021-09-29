+++
title = "Kiểm tra dữ liệu với Athena"
date = 2021
weight = 4
chapter = false
pre = "<b>9.4 </b>"
+++

#### Xác nhận qua Athena

Giờ chúng ta sẽ xác nhận kết quả qua Athena

1. Truy cập đến [giao diện dịch vụ Athena](https://console.aws.amazon.com/athena/home?region=ap-southeast-1#query).
  + Ở khung bên trái, chọn **analyticsworkshopdb** từ phần sổ xuống.
  + Chạy câu lệnh query dưới đây:

```
SELECT track_name as "Track Name",
    artist_name as "Artist Name",
    count(1) as "Hits" 
FROM analyticsworkshopdb.processed_data 
GROUP BY 1,2 
ORDER BY 3 DESC 
LIMIT 5;
```

![Architect](/images/9/10.png?width=90pc)

2. So sánh kết quả query với kết quả từ lambda function, cả 2 sẽ cho kết quả giống nhau.


Qua phần này bạn bây giờ có thể tạo Lambda function và thực hiện truy vấn dữ liệu với Lambda.
Ở phần tiếp theo chúng ta sẽ đi thử xây dựng Data Warehouse trên Amazon Redshift.
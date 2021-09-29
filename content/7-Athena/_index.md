+++
title = "Phân tích với Athena"
date = 2021
weight = 7
chapter = false
pre = "<b>7. </b>"
+++

---

Tiếp đến, chúng ta đã lưu 1 vài data sets ở trong Amazon S3, và cataloged chúng trong AWS Glue Data Catalog. Với Amazon Athena chúng ta sẽ có thể khám phá dữ liệu sử dụng những câu lệnh query SQL cơ bản

![Architect](/images/7/athena.png?width=60pc)



#### Khám phá dữ liệu đã chuyển đổi với Athena

Ở bước này chúng ta sẽ phân tích dữ liệu đã chuyển đổi sử dụng Amazon Athena

1. Truy cập vào [giao diện quản trị của dịch vụ Amazon Athena](https://console.aws.amazon.com/athena/home?region=ap-southeast-1#query)

{{%notice tip%}}
Nếu bạn thấy thông báo yêu cầu bạn trước tiên phải tạo S3 bucket để lưu kết quả query, thì hãy làm theo các bước sau. \
\
Truy cập vào **giao diện quản trị của dịch vụ S3** và tạo 1 bucket sử dụng tên như **yourname-query-results**. \
Sau khi tạo bucket, quay trở lại Athena console và click **Settings** ở góc phải của console. \
Nhập tên bucket bạn vừa tạo, và hãy chắc rằng nó có bao gồm gạch chéo: **s3://yourname-query-results/**. \
Click **Save**.
{{%/notice%}}

2. Athena sử dụng AWS Glue catalog để tiếp tục theo dõi data source, bất kì table S3 nào được hỗ trợ trong Glue đều sẽ hiển thị ở Athena.
  + Ở bên trái, chọn **analyticsworkshopdb**.
  + Chạy câu lệnh query:

```
SELECT artist_name,
       count(artist_name) AS count
FROM processed_data
GROUP BY artist_name
ORDER BY count desc
```

![Architect](/images/7/1.png?width=90pc)

3. Khám phá giao diện của Athena và hãy thử chạy 1 số queries. Thử query table ```emr_processed_data```.

![Architect](/images/7/2.png?width=90pc)

4. Query này sẽ trả về danh sách các bản nhạc được phát nhiều lần bởi các thiết bị. Tiếp theo sau, chúng ta sẽ trực quan hoá query này sử dụng QuickSight:

```
SELECT device_id,
       track_name,
       count(track_name) AS count
FROM processed_data
GROUP BY device_id, track_name
ORDER BY count desc
```

![Architect](/images/7/3.png?width=90pc)

---

Bạn có thể chạy những câu lệnh Athena query quen thuộc và khám phá dữ liệu nhiều hơn.
Ở phần tiếp theo, chúng ta sẽ sử dụng Athena 1 lần nữa để dựng dashboard và trực quan hoá dữ liệu trên Amazon QuickSight.



---
title : "Xác minh các bảng vừa tạo trong catalog"
date :  "`r Sys.Date()`" 
weight : 3
chapter : false
pre : " <b> 4.3 </b> "
---

#### Xác minh các bảng vừa tạo trong catalog

1. Điều hướng đến Glue Catalog và khám phá dữ liệu đã được crawl:

- Đi đến: [](https://console.aws.amazon.com/glue/home?region=us-east-1#catalog:tab=databases)
- Chọn  vào analyticsworkshopdb
- Chọn  vào Tables trong analyticsworkshopdb

![Data Analytics on AWS](/images/4/00021.png?featherlight=false&width=90pc)

2. Chọn  vào raw

![Data Analytics on AWS](/images/4/00022.png?featherlight=false&width=90pc)

3. Dạo quanh và khám phá schema cho tập dữ liệu của bạn tìm kiếm averageRecordSize, recordCount, compressionType

![Data Analytics on AWS](/images/4/00023.png?featherlight=false&width=90pc)

4. Truy vấn dữ liệu đã được nhập vào bằng Amazon Athena

- Hãy truy vấn dữ liệu vừa được nhập vào bằng Amazon Athena
- Đi đến: [](https://us-east-1.console.aws.amazon.com/athena/home?region=us-east-1#query)

![Data Analytics on AWS](/images/4/00024.png?featherlight=false&width=90pc)

5. Nếu cần thiết, hãy Chọn  vào "Edit seetings" trong cảnh báo màu xanh lá cây gần đầu giao diện điều khiển Athena.
Vị trí kết quả truy vấn: Trong mục "Under Query result", chọn s3://yourname-analytics-workshop-bucket/query_results/
Chọn  vào "Save".


![Data Analytics on AWS](/images/4/00025.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/4/00026.png?featherlight=false&width=90pc)


6. Chọn tab "Editor tab".
Trên bảng điều khiển bên trái (Database), chọn analyticsworkshopdb > chọn bảng "raw".
Chọn  vào 3 chấm (3 chấm dọc) > Chọn "Preview Table".
Review kết quả trả về.


![Data Analytics on AWS](/images/4/00027.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/4/00028.png?featherlight=false&width=90pc)

7. Trong trình soạn thảo truy vấn, dán truy vấn sau đây:

```
SELECT activity_type,
         count(activity_type)
FROM raw
GROUP BY  activity_type
ORDER BY  activity_type
```


![Data Analytics on AWS](/images/4/00029.png?featherlight=false&width=90pc)

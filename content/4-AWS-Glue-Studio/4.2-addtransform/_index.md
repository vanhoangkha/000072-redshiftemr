+++
title = "Cấu hình transform"
date = 2020
weight = 2
chapter = false
pre = "<b>4.2 </b>"
+++

#### Cấu hình transform

1. Click chọn bất kì S3 nodes nào trong 2 nodes
+ Click **Transform** và chọn **Join**

![Architect](/images/4/5.png?width=90pc)

2. Click **Transform - Join** node và chọn **Node properties** ở cửa sổ cấu hình bên phải, chọn danh sách sổ xuống và chọn tất cả các S3 data source như màn hình dưới đây:

![Architect](/images/4/6.png?width=90pc)

3. Chuyển qua **Transform** tab.
  + Click **Add condition**.
  + Chọn **track_id** column là column sẽ join như hình dưới.

![Architect](/images/4/7.png?width=90pc)

4. Với **Join** node đang được chọn, Click **Transform** và chọn **ApplyMapping**.

![Architect](/images/4/8.png?width=90pc)

5. Chúng ta sẽ bỏ những cột không sử dụng và map kiểu dữ liệu mới cho column sau:
  + drop Columns
    + .track_id
    + parition_0
    + parition_1
    + parition_2
    + parition_3
  + Map New Data Type
    + track_id **string**
  + Lựa chọn của bạn nên giống hình phía dưới

![Architect](/images/4/9.png?width=90pc)

6. Click **Transform - ApplyMapping** node ở trên màn hình.
  + Sau đó Click **Target** và chọn **S3** như màn hình dưới đây.

![Architect](/images/4/10.png?width=90pc)

7. Ở tab **Data target properties - S3**, cung cấp những giá trị sau đây:
  + Format: **Glue Parquet**.
  + Compression Type: **Snappy**.
  + S3 Target Location: **s3://yourname-analytics-workshop-bucket/data/processed-data2/**.
  + Data Catalog update options
    + Chọn **Create a table in the Data Catalog and on subsequent runs, update the schema and add new partitions**.
  + Database: **analyticsworkshopdb**.
  + Table name: **processed-data2**.

![Architect](/images/4/14.png?width=90pc)

8. Click **Job details** và cấu hình như dưới đây.
  + Name: **AnalyticsOnAWS-GlueStudio**.
  + IAM Role: **AnalyticsWorkshopGlueRole**.
  + Number of workers: **2**.
  + Job bookmark: **Disable**.
  + Number of retries: **1**.
  + Job timeout (minutes): **10**.
  + Còn những giá trị còn lại để mặc định.
  + Click **Save**.

![Architect](/images/4/11.png?width=90pc)

9. Click **Save** và bạn nên thấy **“Successfully created job”**. 

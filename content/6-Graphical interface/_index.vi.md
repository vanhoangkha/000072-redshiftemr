---
title : "Transform Data with AWS Glue Studio (graphical interface)"
date: 2024-01-01
weight : 6
chapter : false
pre : " <b> 6. </b> "
---

#### Transform Data with AWS Glue Studio (graphical interface)

#### Biến đổi dữ liệu với AWS Glue Studio

AWS Glue Studio là một giao diện đồ họa mới giúp việc tạo, chạy và giám sát job trích xuất, biến đổi và tải (ETL) dữ liệu trở nên dễ dàng trong AWS Glue. Bạn có thể hình dung quy trình biến đổi dữ liệu một cách trực quan và chạy chúng trên động cơ ETL serverless của AWS Glue dựa trên Apache Spark.

Trong bài thực hành này, chúng ta sẽ thực hiện quá trình ETL tương tự như Biến đổi dữ liệu với AWS Glue (phiên tương tác).

Nhưng lần này chúng ta sẽ tận dụng giao diện đồ họa trực quan trong AWS Glue Studio!

Sử dụng AWS Glue Data Studio, một giao diện đồ họa giúp việc tạo, chạy và giám sát job trích xuất, biến đổi và tải (ETL) dữ liệu trở nên dễ dàng trong AWS Glue.

1. Đi đến Bảng điều khiển Glue Studio. 

- Chọn  vào biểu tượng hamburger bên trái để mở rộng menu.

![Data Analytics on AWS](/images/6/0001.png?featherlight=false&width=90pc)

2. Click - Jobs và chọn Visual with a blank canvas

- Click Create

![Data Analytics on AWS](/images/6/0002.png?featherlight=false&width=90pc)

3. Click - Source và chọn - S3

![Data Analytics on AWS](/images/6/0003.png?featherlight=false&width=90pc)

4. Chọn  vào tab "Data source properties - S3" trong cửa sổ cấu hình ở phía bên phải màn hình.
- Dưới loại Source S3, chọn "Data Catalog Table".
- Chọn các giá trị sau đây:
- Database - analyticsworkshopdb
- Table - raw

![Data Analytics on AWS](/images/6/0004.png?featherlight=false&width=90pc)

5.  Bây giờ chúng ta sẽ lặp lại các bước tương tự để thêm reference_data từ S3. Chọn  chuột vào - Source và chọn - S3.

![Data Analytics on AWS](/images/6/0005.png?featherlight=false&width=90pc)

6. Chọn  vào tab "Data source properties - S3" trong cửa sổ cấu hình ở phía bên phải màn hình.
- Dưới loại nguồn S3, chọn "Data Catalog table".
- Chọn các giá trị sau đây:
- Database (Cơ sở dữ liệu): analyticsworkshopdb
- Table (Bảng): reference_data

![Data Analytics on AWS](/images/6/0006.png?featherlight=false&width=90pc)

7. Chọn  vào nút S3 đã thêm trước đó trên bảng vẽ, sau đó Chọn  vào Action và chọn Change Schema.

![Data Analytics on AWS](/images/6/0007.png?featherlight=false&width=90pc)

8. Chọn tab "Transform" ở phía bên phải và thay đổi kiểu dữ liệu của "track_id" thành kiểu số nguyên.

![Data Analytics on AWS](/images/6/0008.png?featherlight=false&width=90pc)

9. Chọn  vào nút S3 bên trái trên bảng vẽ.

![Data Analytics on AWS](/images/6/0009.png?featherlight=false&width=90pc)

10. Click Action và chọn Join

![Data Analytics on AWS](/images/6/00010.png?featherlight=false&width=90pc)

11. Bạn nên có biểu đồ hình ảnh như trong ảnh chụp màn hình dưới đây và thông báo bên phải "Insufficient source nodes" vì bạn cần một nút khác (Data source) để kết nối.

Next, Chọn  vào Transform - Join node và trên cửa sổ cấu hình bên phải của Node properties, chọn danh sách thả xuống và chọn Change Schema dưới phần Tramsforms như được mô tả trong ảnh chụp màn hình dưới đây:

![Data Analytics on AWS](/images/6/00011.png?featherlight=false&width=90pc)

12. Chọn  vào tab "Transform" với nút "Join Node" đã được chọn trên bảng vẽ.

- Chọn  vào "Add condition".

- Chọn cột "track_id" làm cột ghép như được hiển thị trong ảnh chụp màn hình dưới đây.

![Data Analytics on AWS](/images/6/00012.png?featherlight=false&width=90pc)

13. Khi đã chọn nút "Join" trên bảng vẽ, Chọn  vào "Action" và chọn "Change Schema".

- Bạn nên có được sơ đồ hình ảnh như trong ảnh chụp màn hình dưới đây.
- Chúng ta sẽ xóa các cột không sử dụng và ánh xạ kiểu dữ liệu mới cho các cột sau:
- drop Columns
- parition_0
- parition_1
- parition_2
- parition_3
- Map New Data Type
- track_id string
- Các lựa chọn của bạn nên phù hợp với hình ảnh màn hình dưới đây:

![Data Analytics on AWS](/images/6/00013.png?featherlight=false&width=90pc)

14.  Chọn  vào nút Transform - ApplyMapping trên màn hình

![Data Analytics on AWS](/images/6/00014.png?featherlight=false&width=90pc)

15. Chọn  vào mục "Target" và chọn S3 như hình minh họa dưới đây.

- Data target properties - S3:
- Format: Parquet
- Compression Type: Snappy
- S3 Target Location: s3://yourname-analytics-workshop-bucket/data/processed-data2/
- Data Catalog update options
- Choose Create a table in the Data Catalog and on subsequent runs, update the schema and add new partitions
- Database: analyticsworkshopdb
- Table name: processed-data2

![Data Analytics on AWS](/images/6/00015.png?featherlight=false&width=90pc)

16. Click Job details và cấu hình:
- Name: AnalyticsOnAWS-GlueStudio
- IAM Role: AnalyticsWorkshopGlueRole
- Requested number of workers: 2
- Job bookmark: Disable
- Number of retries: 1
- Job timeout (minutes): 10
- Leave the rest as default value
- Click Save

![Data Analytics on AWS](/images/6/00016.png?featherlight=false&width=90pc)

17. Chọn  vào "Save" và bạn sẽ thấy thông báo "Successfully created job". Bắt đầu ETL jobs này bằng cách Chọn  vào "Run" ở góc phải trên cùng của màn hình.

![Data Analytics on AWS](/images/6/00017.png?featherlight=false&width=90pc)

18. Bạn nên xem thông báo "Successfully started job". Chọn  vào "Run Details" để theo dõi ETL jobs của bạn. Hãy đợi trong vài giây và bạn sẽ thấy ETL job Run Status "Succeeded", như được hiển thị trong ảnh chụp màn hình dưới đây.

![Data Analytics on AWS](/images/6/00018.png?featherlight=false&width=90pc)

19. Bạn có thể xem mã Pyspark mà Glue Studio đã tạo ra và tái sử dụng mã này cho các mục đích khác nếu cần.

![Data Analytics on AWS](/images/6/00019.png?featherlight=false&width=90pc)

20. Truy cập vào Glue DataCatalog:  và bạn sẽ thấy bảng processed-data2 đã được tạo trong cơ sở dữ liệu analyticsworkshopdb.

![Data Analytics on AWS](/images/6/00020.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/6/00021.png?featherlight=false&width=90pc)

Xuất sắc!! Bạn đã hoàn thành một lab ETL bổ sung với AWS Glue Studio. Với AWS Glue Studio, bạn có thể tổ hợp các luồng làm việc biến đổi dữ liệu một cách trực quan và chạy chúng một cách liền mạch trên nền tảng ETL không cần máy chủ dựa trên Apache Spark của AWS Glue.





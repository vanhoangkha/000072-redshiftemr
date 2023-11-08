---
title : "Transform Data with AWS Glue (interactive sessions)"
date :  "`r Sys.Date()`" 
weight : 5
chapter : false
pre : " <b> 5. </b> "
---

#### Transform Data with AWS Glue (interactive sessions)

Trong module này, chúng ta sẽ sử dụng các AWS Glue (interactive sessions) để xử lý dữ liệu và lưu kết quả trở lại một lớp đã được biến đổi trong S3.

Chúng ta sẽ sử dụng Glue Studio và Jupyter notebooks được cung cấp bởi AWS Glue Interactive Sessions để thực hiện các bước biến đổi dữ liệu.

AWS Glue (interactive sessions) là gì?

Phiên tương tác cho phép bạn phát triển AWS Glue quy trình một cách tương tác, chạy và kiểm tra từng bước và xem kết quả. Nếu bạn thích trải nghiệm dựa trên mã và muốn tạo quy trình tích hợp dữ liệu theo cách tương tác, phiên tương tác là lựa chọn được khuyến nghị.

#### Chuẩn bị  IAM Policies và role

Ghi chú: Bỏ qua phần này nếu bạn đã tạo policy IAM và role Glue trong mô-đun Data Warehouse trên Redshift và chuyển đến phần Sử dụng Jupyter Notebook trong AWS Glue để phát triển ETL tương tác của mô-đun này.

1. Trong bước này, bạn sẽ điều hướng đến bảng điều khiển IAM và tạo các policy IAM và role cần thiết để làm việc với Jupyter notebooks và phiên tương tác của AWS Glue Studio.

- Hãy bắt đầu bằng cách tạo một policy IAM cho role sổ tay AWS Glue.
- Chọn  vào Policies từ bảng điều khiển trên thanh bên trái
- Chọn  vào  Create policy
- Chọn  vào tab JSON
- Thay thế văn bản mặc định trong cửa sổ chỉnh sửa policy bằng các câu lệnh policy sau đây.

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
    "Effect": "Allow",
    "Action": "iam:PassRole",
    "Resource":"arn:aws:iam::<AWS account ID>:role/Analyticsworkshop-GlueISRole"
    }
  ]
}

```


![Data Analytics on AWS](/images/5/0001.png?featherlight=false&width=90pc)

2. Lưu ý rằng Analyticsworkshop-GlueISRole là role chúng ta tạo cho Jupyter notebook AWS Glue Studio trong bước Next.

Cảnh báo: Thay bằng ID tài khoản AWS của bạn trong câu lệnh policy đã sao chép.

- Chọn  vào Next: Tag
- Tùy chọn thêm tag, ví dụ:workshop: AnalyticsOnAWS
- Chọn  vào Next: Review
- Policy name: AWSGlueInteractiveSessionPassRolePolicy
- Tùy chọn viết mô tả cho policy:
- Mô tả: policy cho phép role của notebook AWS Glue chuyển cho các phiên tương tác để cùng một role có thể được sử dụng ở cả hai nơi
- Chọn  vào Create Policy

![Data Analytics on AWS](/images/5/0002.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/5/0003.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/5/0004.png?featherlight=false&width=90pc)

3. Chọn  vào Roles từ thanh bên trái
- Chọn  vào Create role
- Chọn dịch vụ sẽ sử dụng role này: Glue dưới Use Case và Use cases for other AWS services:
- Chọn  vào Next


![Data Analytics on AWS](/images/5/0005.png?featherlight=false&width=90pc)

4. Tìm kiếm các policy sau và chọn ô đánh dấu bên cạnh chúng:
- AWSGlueServiceRole
- AwsGlueSessionUserRestrictedNotebookPolicy
- AWSGlueInteractiveSessionPassRolePolicy
- AmazonS3FullAccess
- Chọn  vào Next


![Data Analytics on AWS](/images/5/0006.png?featherlight=false&width=90pc)

5. Tên role: Analyticsworkshop-GlueISRole
- Đảm bảo chỉ có bốn policy được gắn kết vào role này (AWSGlueServiceRole, AwsGlueSessionUserRestrictedNotebookPolicy, AWSGlueInteractiveSessionPassRolePolicy, AmazonS3FullAccess)


![Data Analytics on AWS](/images/5/0007.png?featherlight=false&width=90pc)

6. Tùy chọn thêm các Tags (nhãn), ví dụ: workshop: AnalyticsOnAWS
- Chọn  vào Create role

![Data Analytics on AWS](/images/5/0009.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00010.png?featherlight=false&width=90pc)

#### Sử dụng Jupyter Notebook trong AWS Glue cho việc phát triển ETL tương tác

1. Trong bước này, bạn sẽ tạo một job AWS Glue với Jupyter Notebook để phát triển tương tác các script Glue ETL bằng PySpark.

- Tải xuống và lưu tệp:  [analytics-workshop-glueis-notebook.ipynb](https://static.us-east-1.prod.workshops.aws/public/9b2d1982-fdcf-4207-ba26-71a458796115/static/notebooks/analytics-workshop-glueis-notebook.ipynb) hoặc [Github](https://raw.githubusercontent.com/AWS-First-Cloud-Journey/Lab-72--Analytics-workshop-on-AWS/master/analytics-workshop-glueis-notebook.ipynb)
- Đi đến:  Glue Studio Jobs
- Chọn tùy chọn Jupyter Notebook
- Chọn **Upload and edit an existing notebook**
- Chọn  vào Choose file


![Data Analytics on AWS](/images/5/00011.png?featherlight=false&width=90pc)

2. Duyệt và tải lên analytics-workshop-glueis-notebook.ipynb mà bạn đã tải xuống trước đó
- Chọn  vào  Create


![Data Analytics on AWS](/images/5/00012.png?featherlight=false&width=90pc)

3. Dưới Notebook setup và Initial configuration
- Job name: AnalyticsOnAWS-GlueIS
- IAM role Analyticsworkshop-GlueISRole
- Leave Kernel to default as Spark
- Click Start notebook

![Data Analytics on AWS](/images/5/00013.png?featherlight=false&width=90pc)

4. Khi notebook được khởi tạo, làm theo các hướng dẫn trong notebook. Bạn quan sát và chạy notebook theo hình.

![Data Analytics on AWS](/images/5/00014.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00015.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00016.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00017.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00018.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00019.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00020.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00021.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00022.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00023.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00024.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00025.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00026.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00027.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00028.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00029.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00030.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/5/00032.png?featherlight=false&width=90pc)

#### Dữ liệu đã được xác thực - đã được chuyển đổi / xử lý và đã đến S3


1. Chọn  vào - yourname-analytics-workshop-bucket > data
- Mở thư mục processed-data:

![Data Analytics on AWS](/images/5/0033.png?featherlight=false&width=90pc)

2. Đảm bảo rằng các tệp .parquet đã được tạo trong thư mục này.
- Bây giờ chúng ta đã chuyển đổi dữ liệu, chúng ta có thể truy vấn dữ liệu bằng cách sử dụng Amazon Athena. Chúng ta cũng có thể tiếp tục chuyển đổi/tổng hợp dữ liệu bằng AWS Glue hoặc Amazon EMR.

![Data Analytics on AWS](/images/5/00034.png?featherlight=false&width=90pc)

Mô-đun Next về EMR là tùy chọn. Bạn có thể bỏ qua nó nếu muốn và tiếp tục phân tích bằng Athena.
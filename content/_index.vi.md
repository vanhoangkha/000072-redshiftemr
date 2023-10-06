---
title : "Analytics on AWS workshop"
date :  "`r Sys.Date()`" 
weight : 1 
chapter : false
---

# Analytics on AWS workshop


Chào mừng bạn đến với workshop về Analytics trên AWS. Workshop này đã được thiết kế để giúp bạn làm quen với các dịch vụ phân tích khác nhau có trong danh mục AWS Analytics.

Workshop sẽ đi qua một chuỗi các module, bao gồm các khía cạnh khác nhau của việc xây dựng một nền tảng phân tích trên AWS. Bạn sẽ được học cách tiếp nhận, lưu trữ, chuyển đổi và tiêu thụ dữ liệu bằng một số dịch vụ phân tích như AWS Glue, Amazon Athena, Amazon Kinesis, Amazon EMR, Amazon QuickSight cùng với AWS Lambda và Amazon Redshift.

Một biểu đồ chi tiết hơn về thiết kế được trình bày trong kiến trúc dưới đây -

![Data Analytics on AWS](/images/0/0001.png?featherlight=false&width=60pc)


Kết quả học tập từ workshop này:

1. Thiết kế kiến trúc Data Lake serverless (serverless data lake).
2. Xây dựng đường ống xử lý dữ liệu và Data Lake bằng cách sử dụng Amazon S3 để lưu trữ dữ liệu.
3. Sử dụng Amazon Kinesis để xử lý dữ liệu trực tiếp (real-time streaming data).
4. Sử dụng Amazon Kinesis Data Analytics để phân tích dữ liệu trực tiếp (real-time data analysis).
5. Sử dụng AWS Glue để tự động lưu trữ dữ liệu trong danh mục (catalog datasets).
6. Chuyển đổi dữ liệu (Data Transformation).
7. Chạy các script ETL tương tác trong Jupyter notebook trên AWS Glue Studio bằng cách sử dụng phiên tương tác của AWS Glue.
8. Sử dụng Glue Studio để chạy và giám sát các ETL jobs trên AWS Glue.
9. Sử dụng Glue DataBrew để chuẩn bị dữ liệu.
10. Sử dụng EMR để chạy job biến đổi Spark.
11. Tải dữ liệu lên Amazon Redshift từ Glue.
12. Giới thiệu về các phương pháp thiết kế tốt nhất của Amazon Redshift.
13. Truy vấn dữ liệu bằng Amazon Athena và trực quan hóa nó bằng Amazon QuickSight. 
14. Dọn dẹp tài nguyên
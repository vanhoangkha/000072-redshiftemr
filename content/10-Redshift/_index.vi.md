+++
title = "Warehouse trên Redshift"
date = 2020
weight = 10
chapter = false
pre = "<b>10. </b>"
+++

---

Ở phần này, chúng ta sẽ thiết lập một Amazon Redshift cluster, và sử dụng AWS Glue để load dữ liệu vào Amazon Redshift. Chúng ta sẽ tìm hiểu về một số thiết kế và các phương pháp tốt nhất để tải dữ liệu vào table trong Redshift, và chạy queries trên nó.

![Architect](/images/10/redshift.png?width=60pc)

#### Nội dung

1. [Tạo Redshift IAM role](10.1-createiamrole/)
2. [Tạo Redshift cluster](10.2-createcluster/)
3. [Tạo S3 Gateway Endpoint](10.3-s3gateway/)
4. [Cấu hình Security Group](10.4-configuresecgroup/)
5. [Tạo Redshift connection](10.5-glueconnection/)
6. [Tạo schema và tables](10.6-createschema/)
7. [Chuyển đổi và load dữ liệu](10.7-extractloaddata/)
8. [Kiểm tra dữ liệu](10.8-reviewdata/)
9. [Tối ưu Redshift](10.9-optimizeredshift/)
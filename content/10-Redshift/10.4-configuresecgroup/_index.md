+++
title = "Cấu hình Security group"
date = 2021
weight = 4
chapter = false
pre = "<b>10.4 </b>"
+++

#### Xác nhận và thêm rule vào security group mặc định

Ở bước này, chúng ta sẽ xác nhận và thêm rule cho Redshift security group để dịch vụ Glue có thể làm việc được với Redshift.

1. Truy cập đến [giao diện quản trị dịch vụ VPC: security groups](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#SecurityGroups:sort=tag:Name).
  + Chọn Redshift security group. Nó sẽ ở security mặc định nếu nó không thay đổi khi chúng ta tạo Redshift cluster.
  + Nếu bạn có nhiều hơn 1 security group trong danh sách, làm theo những bước sau:
    + Truy cập đến [giao diện quản trị dịch vụ Redshift](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1).
    + Click **redshift-cluster-1**.
    + Click tab **Properties**.
    + Kéo xuống và kiểm tra phần **Network and security** để lấy Security Group id.
  + Một khi bạn đã xác nhận Security Group, chọn security group.
  + Click **Inbound rules**.
  + Click **Edit rules**.

![Architect](/images/10/8.png?width=90pc)

2. Kiểm tra rule có sẵn.
    + Type: All Traffic.
    + Source: [Tên của security group bạn đang edit].

{{% notice note %}}
Rule tự tham chiếu này là cần thiết để Glue có thể giao tiếp với Redshift.
{{% /notice %}}

  + Thêm **HTTPS** rule cho Amazon S3 access.
    + Type: ```HTTPS```.
    + Source: [s3-prefix-list-id].

{{% notice note %}}
Dưới phần **Source** chọn Custom và nhập "pl vào text box cạnh nó, S3 endpoint tạo trước đó sẽ hiển thị và chọn nó.
{{% /notice %}}

  + Click **Save rules**.

![Architect](/images/10/9.png?width=90pc)

  + Click **Outbound Rules**.
  + Click **Edit rules**.

![Architect](/images/10/10.png?width=90pc)

  + Để nguyên rule với những giá trị dưới đây:
    + Type: All Traffic
    + Source: ```0.0.0.0/0```
  + Rule tự tham chiếu
    + Type: All TCP
    + Source: [Tên của security group bạn đang edit] 
  + Click **Save rules**.

![Architect](/images/10/11.png?width=90pc)

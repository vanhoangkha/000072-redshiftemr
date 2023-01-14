+++
title = "Tạo S3 Gateway Endpoint"
date = 2021
weight = 3
chapter = false
pre = "<b>10.3 </b>"
+++


#### Tạo S3 Gateway Endpoint

Ở bước này, chúng ta sẽ tạo S3 Gateway Endpoint để Redshift cluster có thể giao tiếp với S3 sử dụng private IP

1. Truy cập đến [giao diện quản trị của dịch vụ VPC](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#Endpoints:sort=vpcEndpointId).
  + Click **Create Endpoint**.

![Data Analysis on AWS](/images/10/13.png?featherlight=false&width=90pc)

2. Chọn **AWS Service** dưới **Service category**.

![Data Analysis on AWS](/images/10/14.png?featherlight=false&width=90pc)

  + Dưới **Service name** trong khung tìm kiếm, tìm **S3** và Click enter.
  + **com.amazonaws.ap-southeast-1.s3** sẽ hiển ra dưới kết quả tìm kiếm. Chọn tuỳ chọn này.
  + Tại mục **VPC**, chọn VPC mặc định. Đây cũng là VPC sử dụng khi cấu hình redshift cluster.
  + Nếu có nhiều hơn 1 VPC được liệt kê, hãy kiểm tra VPC của Redshift để tránh nhầm lẫn.
    + Đi đến: Redshift console [Click vào đây](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1).
    + Click **redshift-cluster-1**.
    + Click tab **Properties**.
    + Kéo xuống và kiểm tra phần **Network and security** để tìm tên của VPC.
  + Khi bạn đã check VPC xong, đi đến phần **Configure route tables**.
  + Chọn list route table (nó nên là các main route table). Bạn có thể xác nhận bằng cách check **Yes** dưới các **Main** column.


![Data Analysis on AWS](/images/10/15.png?featherlight=false&width=90pc)

3. Để **Policy** mặc định (**Full Access**)

![Data Analysis on AWS](/images/10/16.png?featherlight=false&width=90pc)


{{% notice note %}}
**com.amazonaws.ap-southeast-1.s3** id được liệt kê lần nữa ở **Configure route tables**. Nó nên bắt đầu với pl-[some number]
{{% /notice %}}


4. Click **Create endpoint**.

![Data Analysis on AWS](/images/10/17.png?featherlight=false&width=90pc)

5. Việc này sẽ tốn vài giây để khởi tạo. Một khi đã sẵn sàng, bạn sẽ thấy **Status** là **Available**.

![Data Analysis on AWS](/images/10/18.png?featherlight=false&width=90pc)





+++
title = "Tạo Redshift cluster"
date = 2021
weight = 2
chapter = false
pre = "<b>10.2 </b>"
+++


#### Tạo Redshift cluster

Ở bước này, chúng ta sẽ tạo 2 node Redshift cluster để tạo một star schema database nhỏ.

1. Truy cập đến [giao diện quản trị dịch vụ Redshift](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1)
  + Click **Create Cluster**.


![Data Analysis on AWS](/images/10/7.png?featherlight=false&width=90pc)

2. Để **Cluster identifier** là **redshift-cluster-1**.
  + Chọn **Node Type** là **dc2.large**.
  + Chọn **Number of Nodes** là ```2```.
  + Xác nhận **Configuration summary**.

![Data Analysis on AWS](/images/10/8.png?featherlight=false&width=90pc)

3.  Để **Database port(optional)** là **5439**.
  + Thay đổi **Master user name** thành ```admin```.
  + Nhập **Master user password** .
  + Kiểm tra các luật đặt password trước khi chọn password (**Password này sẽ sử dụng để truy cập vào cluster**).

![Data Analysis on AWS](/images/10/9.png?featherlight=false&width=90pc)

4. Mở rộng phần **Clusster permissions (optional)**.
    + Chọn role đã tạo từ trước **Analyticsworkshop_RedshiftRole**.
    + Click **Add IAM Role**.
    + **Analyticsworkshop_RedshiftRole** sẽ hiển thị dưới **Attached IAM roles**.

![Data Analysis on AWS](/images/10/10.png?featherlight=false&width=90pc)

5. Để **Additional configurations** mặc định. Nó sẽ sử dụng VPC mặc định và security group mặc định
  + Click **Create Cluster**. CHúng ta sẽ tốn vài phút để cluster đổi qua trạng thái ```available```.

![Data Analysis on AWS](/images/10/11.png?featherlight=false&width=90pc)

Khi cluster đã tạo và trạng thái là Available, hãy đi đến bước tiếp theo.

![Data Analysis on AWS](/images/10/12.png?featherlight=false&width=90pc)
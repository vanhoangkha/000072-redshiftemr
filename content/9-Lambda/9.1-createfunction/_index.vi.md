+++
title = "Tạo Lambda Function"
date = 2021
weight = 1
chapter = false
pre = "<b>9.1 </b>"
+++

#### Tạo Lambda Function

1. Truy cập đến [giao diện quản trị của dịch vụ Lambda](https://console.aws.amazon.com/lambda/home?region=ap-southeast-1).
  + **Note**: Hãy chắc chắn Region đang được chọn là Singapore ap-southeast-1

![Data Analysis on AWS](/images/9/1.png?featherlight=false&width=90pc)

2. Nhấn **Create function** (Nếu bạn sử dụng Lambda lần đầu, bạn nên nhấn Get Started để tiến hành).
  + Chọn **Author from scratch**.
  + Tại mục **Basic Information**:
  + Cho Function name là ```Analyticsworkshop_top5Songs```.
  + Chọn Runtime là **Python 3.8**.


![Data Analysis on AWS](/images/9/2.png?featherlight=false&width=90pc)

3. Mở rộng **Choose or create an execution role** dưới Permissions, hãy chắc rằng **Create a new role with basic Lambda permissions** được chọn.
  + Nhấn **Create Function**.


![Data Analysis on AWS](/images/9/3.png?featherlight=false&width=90pc)




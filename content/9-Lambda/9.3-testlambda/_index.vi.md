+++
title = "Truy vấn dữ liệu với Lambda"
date = 2021
weight = 3
chapter = false
pre = "<b>9.3 </b>"
+++

#### Truy vấn dữ liệu với Lambda

Function của chúng ta bây giờ đã sẵn sàng để test. 

1. Deploy function bằng cách nhấn nút **Deploy**.


![Data Analysis on AWS](/images/9/12.png?featherlight=false&width=90pc)

2. Cấu hình test lambda function để xem kết quả chạy của lambda function mới tạo.
  + Nhấn **Test** ở trên góc phải của phần **Code Source**.

![Data Analysis on AWS](/images/9/13.png?featherlight=false&width=90pc)


3. Ở cửa sổ mới bật lên cấu hình test event.
  + **Create new test event** được chọn mặc định.
  + Event template: **Hello World**.
  + Event name: **Test**.
  + Để nguyên những thứ khác.
  + Nhấn **Create**.

![Data Analysis on AWS](/images/9/14.png?featherlight=false&width=90pc)

4. Nhấn **Test** lần nữa
  + Bạn sẽ thấy output ở định dạng json ở dưới phần **Execution Result**.


![Data Analysis on AWS](/images/9/15.png?featherlight=false&width=90pc)

Tiếp theo chúng ta sẽ kiểm tra xem dữ liệu từ Lambda function có giống như dữ liệu được truy vấn từ Athena không nhé.







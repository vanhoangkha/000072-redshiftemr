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

2. Cấu hình test lambda function để xem kết quả chạy của lambda function mới tạo.
  + Nhấn **Test** ở trên góc phải của phần **Code Source**.

![Architect](/images/9/7.png?width=90pc)

3. Ở cửa sổ mới bật lên cấu hình test event.
  + **Create new test event** được chọn mặc định.
  + Event template: **Hello World**.
  + Event name: **Test**.
  + Để nguyên những thứ khác.
  + Nhấn **Create**.

![Architect](/images/9/8.png?width=90pc)

3. Nhấn **Test** lần nữa
  + Bạn sẽ thấy output ở định dạng json ở dưới phần **Execution Result**.

![Architect](/images/9/9.png?width=90pc)

Tiếp theo chúng ta sẽ kiểm tra xem dữ liệu từ Lambda function có giống như dữ liệu được truy vấn từ Athena không nhé.
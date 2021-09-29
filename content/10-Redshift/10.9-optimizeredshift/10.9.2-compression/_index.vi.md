+++
title = "Compression"
date = 2021
weight = 2
chapter = false
pre = "<b>10.9.2 </b>"
+++

#### Compression

Ở bước này, chúng ta sẽ phân tích table raw để chọn giải thuật compression ( nén ) phù hợp.

1. Kiểm tra thuật toán thích hợp trên mỗi bảng để thực hiện compression.
  + Compression là một hoạt động ở cấp độ cột để giảm kích thước của dữ liệu khi nó được lưu trữ. Compression giúp tối ưu không gian lưu trữ và giảm kích thước của dữ liệu được đọc từ bộ lưu trữ, đồng thời làm giảm số lượng I / O vào disk và cải thiện hiệu suất truy vấn.
  + Chạy câu query dưới đây trong giao diện Query Editor.

```
analyze compression redshift_lab.f_raw_1;
```

![Architect](/images/10/24.png?width=90pc)

2. Kết quả từ bảng trên cung cấp thông tin sau cho từng cột:

  + Tên Cột
    + Encoding: Kiểu compression được đề xuất dựa trên loại và giá trị độ chính xác của cột.
    + Est_reduction_pct: Phần trăm giảm ước tính nếu phương thức compression đề xuất được triển khai.

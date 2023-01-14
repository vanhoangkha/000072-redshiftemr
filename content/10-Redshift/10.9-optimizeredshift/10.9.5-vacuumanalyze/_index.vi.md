+++
title = "Vacuum và Analyze"
date = 2021
weight = 5
chapter = false
pre = "<b>10.9.5 </b>"
+++

#### Thực hiện Vacuum và Analyze

1. Ở bước này chúng ta sẽ chạy vacuum và analyze trên table mới chúng ta vừa tạo.

**VACUUM**: Sắp xếp lại các hàng và lấy lại không gian trong một bảng được chỉ định hoặc tất cả các bảng trong cơ sở dữ liệu chỉ định.

**ANALYZE**: Cập nhật thống kê bảng để hệ thống **query planner** sử dụng, nhằm tối ưu hóa cách thức Redshift truy vấn dữ liệu.

2. Chạy câu query dưới đây trong Query Editor.

```
vacuum redshift_lab.f_raw_2;
analyze redshift_lab.f_raw_2;  

```
![Data Analysis on AWS](/images/10/61.png?featherlight=false&width=90pc)

3. Tiếp tục

```
vacuum redshift_lab.d_ref_data_2;
analyze redshift_lab.d_ref_data_2;
```
![Data Analysis on AWS](/images/10/62.png?featherlight=false&width=90pc)

Tiếp theo, chúng ta sẽ thực hiện truy vấn dữ liệu trên bảng mới sau tất cả những thao tác chúng ta đã tối ưu.

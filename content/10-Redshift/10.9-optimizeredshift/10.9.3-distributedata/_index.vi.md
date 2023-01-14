+++
title = "Phân phối dữ liệu"
date = 2021
weight = 3
chapter = false
pre = "<b>10.9.3 </b>"
+++

#### Distribution Style và Sort Keys ( Các kiểu phân phối / sắp xếp dữ liệu )

Distribution / Phân phối dữ liệu là một phương thức tối ưu hiệu năng quan trọng trên Redshift. Việc phân phối dữ liệu tốt sẽ làm giảm lượng dữ liệu phải di chuyển qua lại giữa các node trong Redshift cluster.

1. Chúng ta sẽ sử dụng phân phối dựa trên **KEY** cho bảng dữ kiện **f_raw_1**.
  + Vì hai bảng (**f_raw_1** và **d_ref_data_1**) cần được kết hợp trên cột **track_id**, nên chúng ta sẽ chọn **track_id** làm distribution key.
  

2. Chúng ta sẽ sử dụng phân phối **ALL** cho bảng dimension - **d_ref_data_1**.

3. Tìm hiểu thêm về Redshift Distribution style [tại đây](https://docs.aws.amazon.com/redshift/latest/dg/c_choosing_dist_sort.html).

4. Trong các truy vấn của chúng ta, thuộc tính **activity_type** đã được sử dụng để lọc equality, do đó, chúng ta sẽ chọn thuộc tính này làm cột sắp xếp.
  + Việc lựa chọn cột hay dùng để lọc ( filter ) làm cột để sắp xếp các dữ liệu trong table sẽ giúp câu truy vấn trở nên nhanh hơn.

5. Tìm hiểu thêm về các best practices khi sử dụng sort key của Redshift [tại đây](https://docs.aws.amazon.com/redshift/latest/dg/c_best-practices-sort-key.html)


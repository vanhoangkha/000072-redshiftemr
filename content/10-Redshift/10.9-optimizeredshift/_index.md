+++
title = "Tối ưu Redshift"
date = 2021
weight = 9
chapter = false
pre = "<b>10.9 </b>"
+++

#### Tối ưu Redshift

Ở bước này, húng ta sẽ làm một số best practices của redshift bằng cách optimize nơi lưu trữ và hiệu năng của cluster dựa trên các câu lệnh query chạy trên Redshift cluster

**Mặc dù hầu hết các bước bạn sẽ thực hiện bên dưới đều được tự động hóa trong Redshift nhưng bạn sẽ tốt hơn nếu bạn luôn hiểu được các khái niệm chính và cách chúng hoạt động**

#### Nội dung

1. [Tối ưu kích thước cột](10.9.1-stringcolumnsize/)
2. [Áp dụng compression](10.9.2-compression/)
3. [Phân phối dữ liệu](10.9.3-distributedata/)
4. [Tạo table mới](10.9.4-createnewtable/)
5. [Vacuum và Analyze](10.9.5-vacuumanalyze/)
6. [Query và so sánh hiệu năng](10.9.6-testquery/)
+++
title = "Tối ưu Kích thước cột"
date = 2021
weight = 1
chapter = false
pre = "<b>10.9.1 </b>"
+++

#### Kích thước cột cho dữ liệu chuỗi.

1. Truy cập [giao diện Query Editor của dịch vụ Redshift](https://ap-southeast-1.console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1#query-editor).

  + Chúng ta sẽ thực hiện kiểm tra độ dài tối đa của các cột dựa trên chuỗi.
  + Tất cả các cột dựa trên chuỗi không nên được cấp kích thước to hơn cần thiết. Nó giúp giảm dung lượng lưu trữ trên Redshift cluster và cũng cải thiện hiệu suất truy vấn khi bạn sử dụng các cột này trong truy vấn bằng cách tiêu tốn ít bộ nhớ hơn.

```
select max(len(uuid)) as uuid_len, max(len(activity_type)) as activity_type_len from redshift_lab.f_raw_1;
      
select max(len(track_name)) as uuid_len, max(len(artist_name)) as activity_type_len from redshift_lab.d_ref_data_1;
```

![Data Analysis on AWS](/images/10/57.png?featherlight=false&width=90pc)

2.  Kết quả từ truy vấn trên sẽ được sử dụng để xác định độ chính xác mới cho các cột có dữ liệu dạng chuỗi.

![Data Analysis on AWS](/images/10/58.png?featherlight=false&width=90pc)

3. Tham khảo thêm về việc giới hạn kích thước cột [tại đây](https://docs.aws.amazon.com/redshift/latest/dg/c_best-practices-smallest-column-size.html).
+++
title = "Kiểm tra EMR Job "
date = 2021
weight = 3
chapter = false
pre = "<b>6.3 </b>"
+++

#### Kiểm tra trạng thái của Transform Job chạy trên EMR

1. EMR cluster sẽ tốn 6-8 phút để khởi tạo, và một vài phút để hoàn thành Spark script.
  + Cluster sẽ tự xoá sau khi Spark job chạy xong.
  + Để check trạng thái của job, Click vào Cluster name: **analytics-workshop-transformer**.
  + Đi đến tab **Steps**.
  + Ở đây bạn sẽ thấy 2 thành phần: **Spark application** và **Setup hadoop debugging**.
  + Trạng thái của **Spark application** sẽ chuyển từ **Pending** đến **Running** rồi **Completed**.

![Architect](/images/6/6.png?width=90pc)

2. Khi Spark job đã chạy xong, EMR cluster sẽ bị xoá.
  + Dứoi EMR > Cluster, bạn sẽ thấy trạng thái của cluster là **Terminated** với thông báo **All steps completed**.

![Architect](/images/6/7.png?width=90pc)

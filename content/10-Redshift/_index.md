+++
title = "Warehouse trên Redshift"
date = 2020
weight = 10
chapter = false
pre = "<b>10. </b>"
+++

---

Ở phần này, chúng ta sẽ thiết lập một Amazon Redshift cluster, và sử dụng AWS Glue để load dữ liệu vào Amazon Redshift. Chúng ta sẽ tìm hiểu về một số thiết kế và các phương pháp tốt nhất để tải dữ liệu vào table trong Redshift, và chạy queries trên nó.

![Architect](/images/10/redshift.png?width=90pc)

---

#### Yêu cầu trước bài lab

Hoàn thành những phần trước

+ Lấy và lưu dữ liệu
+ Catalog dữ liệu


---

#### Tạo Redshift IAM role

Ở bước này chúng ta sẽ tạo IAM role cho Redshift cluster

+ Đi đến: IAM console [Nhấn vào đây](https://console.aws.amazon.com/iam/home?region=ap-southeast-1#/roles)
  + Nhấn **Create role**
  + Chọn **Redshift**
  + Chọn **Redshift - customizable** dưới phần **Select your use case**

![Architect](/images/10/1.png?width=90pc)

  + Nhấn **Next: Permissions**
  + Ở thanh tìm kiếm, tìm và check những policies sau:
    + **AmazonS3FullAccess**
    + **AWSGlueConsoleFullAccess**
  + Nhấn **Next: Tags**
    + Tuỳ chọn thêm Tags:
      + workshop: AnalyticsOnAWS
    + Nhấn **Next: Review**

![Architect](/images/10/2.png?width=90pc)

  + Cho **Role Name** là ```Analyticsworkshop_RedshiftRole```
  + Xác nhận 2 policies dưới đây đã được gắn
    + **AmazonS3FullAccess**
    + **AWSGlueConsoleFullAccess**
  + Nhấn **Create Role**

![Architect](/images/10/3.png?width=90pc)

---

#### Tạo Redshift cluster

Ở bước này, chúng ta sẽ tạo 2 node Redshift cluster để tạo một star schema database nhỏ.

+ Đi đến: Console [Nhấn vào đây](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1)
+ Nhấn **Create Cluster**
+ Để **Cluster identifier** là **redshift-cluster-1**
+ Chọn **Node Type** là **dc2.large**
+ Chọn **Number of Nodes** là ```2```
+ Xác nhận **Configuration summary**

![Architect](/images/10/4.png?width=90pc)

+ Để **Database port(optional)** là **5439**
+ Thay đổi **Master user name** thành ```admin```
+ Nhập **Master user password** 
  + Kiểm tra các luật đặt password trước khi chọn password (**Password này sẽ sử dụng để truy cập vào cluster**)
+ Mở rộng phần **Clusster permissions (optional)**
  + Chọn role đã tạo từ trước **Analyticsworkshop_RedshiftRole**
  + Nhấn **Add IAM Role**
  + **Analyticsworkshop_RedshiftRole** sẽ hiển thị dưới **Attached IAM roles**

![Architect](/images/10/5.png?width=90pc)

+ Để **Additional configurations** mặc định. Nó sẽ sử dụng VPC mặc định và security group mặc định
+ Nhấn **Create Cluster**. CHúng ta sẽ tốn vài phút để clustẻ đổi qua trạng thái ```available```
 **Khi cluster đã tạo và trạng thái là Available, hãy đi đến bước tiếp theo**

---

#### Tạo S3 Gatewat Endpoint

Ở bước này, chúng ta sẽ tạo S3 Gateway Endpoint để Redshift cluster có thể giao tiếp với S3 sử dụng private IP

+ Đi đến: AWS VPC console [Nhấn vào đây](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#Endpoints:sort=vpcEndpointId)
+ Nhấn **Create Endpoint**
+ Chọn **AWS Service** dưới **Service category**
+ Dưới **Service name** trong khung tìm kiếm, tìm **S3** và nhấn enter
+ **com.amazonaws.ap-southeast-1.s3** sẽ hiển ra dưới kết quả tìm kiếm. Chọn tuỳ chọn này
+ Dứoi **VPC**, chọn VPC mặc định. Đây cũng là VPC sử dụng khi cấu hình redshift cluster
  + Nếu có nhiều hơn 1 VPC được liệt kê, hãy kiểm tra VPC của Redshift để tránh việc bị rối.
    + Đi đến: Redshift console [Nhấn vào đây](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1)
    + Nhấn **redshift-cluster-1**
    + Nhấn tab **Properties**
    + Kéo xuống và kiểm tra phần **Network and security** để tìm tên của VPC.

![Architect](/images/10/6.png?width=90pc)

  + Khi bạn đã check VPC xong, đi đến phần **Configure route tables**
  + Chọn list route table (nó nên là các main route table). Bạn có thể xác nhận bằng cách check **Yes** dưới các **Main** column

{{% notice note %}}
**com.amazonaws.ap-southeast-1.s3** id được liệt kê lần nữa ở **Configure route tables**. Nó nên bắt đầu với pl-[some number]
{{% /notice %}}

  + Để **Policy** mặc định (**Full Access**)
  + Nhấn **Create endpoint**. Việc này sẽ tốn vài giây để khởi tạo. Một khi đã sẵn sàng, bạn sẽ thấy **Status** là **Available**.
  
![Architect](/images/10/7.png?width=90pc)

---

#### Xác nhận và thêm rule vào security group mặc định

Ở bước này, chúng ta sẽ xác nhận và thêm rule cho Redshift security group để dịch vụ Glue có thể làm việc được với Redshift

+ Đi đến: VPC security groups [Nhấn vào đây](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#SecurityGroups:sort=tag:Name)
+ Chọn Redshift security group. Nó sẽ ở security mặc định nếu nó không thay đổi khi chsung ta tạo Redshift cluster
  + Nếu bạn có nhiều hơn 1 security group trong danh sách, làm theo những bước sauL
    + Đi đến: Redshift Console [Nhấn vào đây](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1)
    + Nhấn **redshift-cluster-1**
    + Nhấn tab **Properties**
    + Kéo xuống và kiểm tra phần **Network and security** để lấy Security Groupd id
+ Một khi bạn đã xác nhận Security Group, chọn security group
+ Nhấn **Inbound rules**
  + Nhấn **Edit rules**

![Architect](/images/10/8.png?width=90pc)

  + Kiểm tra rule có sẵn
    + Type: All Traffic
    + Source: [Tên của security group bạn đang edit]

{{% notice note %}}
Rule tự tham chiếu này là Cần thiết để Glue có thể giao tiếp với Redshift
{{% /notice %}}

  + Thêm **HTTPS** rule cho Amazon S3 access
    + Type: ```HTTPS```
    + Source: [s3-prefix-list-id]

{{% notice note %}}
Dưới phần **Source** chọn Custom và nhập "pl vào text box cạnh nó, S3 endpoint tạo trước đó sẽ hiển thị và chọn nó
{{% /notice %}}

  + Nhấn **Save rules**

![Architect](/images/10/9.png?width=90pc)

+ Nhấn **Outbound Rules**
  + Nhấn **Edit rules**

![Architect](/images/10/10.png?width=90pc)

  + Để nguyên rule với những giá trị dưới đây:
    + Type: All Traffic
    + Source: ```0.0.0.0/0```
  + Rule tự tham chiếu
    + Type: All TCP
    + Source: [Tên của security group bạn đang edit] 
  + Nhấn **Save rules**.

![Architect](/images/10/11.png?width=90pc)

---

#### Tạo Redshift connection thông qua Glue connection

Ở bước này, chúng ta sẽ tạo một Redshift Connection thông qua Glue connection thứ mà bạn sẽ sử dụng trong Development Endpoint để tạo ra đường kết nối đến Redshift

+ Đi đến: Glue Connection Console [Nhấn vào đây](https://us-east-1.console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=connections)
  + Nhấn **Add Connection**
    + Cho **Connection name** là ```analytics_workshop```
    + Chọn **Connection type** là **Amazon Redshift**
    + Nhấn **Next**

![Architect](/images/10/12.png?width=90pc)

  + Thiết lập kết nối vào data store:
    + Chọn **Cluster** là **redshift-cluster-1**
    + Database name và Username sẽ được tự động tạo là dev và admin
    + **Password**: Nhập password mà bạn cấp khi tạo Redshift cluster
    + Nhấn **Next**
    + Sau đó xem lại các thông tin chi tiết của kết nối và nhấn **Finish**

![Architect](/images/10/13.png?width=90pc)

  + Chúng ta sẽ test kết nối này:
    + Chọn kết nối **analytics_workshop**
    + Nhấn **Test Connection**

![Architect](/images/10/14.png?width=90pc)

  + Chọn Glue role tạo trong phần **Catalog dữ liệu** là **AnalyticsworkshopGlueRole**
  + Nhấn **Test Connection**

![Architect](/images/10/15.png?width=90pc)

Việc này sẽ tốn một ít thời gian. Kết nối thành công sẽ hiện lên màn hình thông báo: **analytics_workshop connected successfully to your instance**

---

#### Tạo schema và redshift tables

+ Đi đến: Redshift Query Editor [Nhấn vào đây](https://us-east-1.console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1#query-editor)
+ Chạy câu query dưới đây để tạo schema và table cho dữ liệu raw và reference
+ Nhập thông tin database connection
+ Nhấn **Connect**

![Architect](/images/10/16.png?width=90pc)

```
--	Create redshift_lab schema.
CREATE schema redshift_lab;
```

![Architect](/images/10/17.png?width=90pc)

```
--	Create f_raw_1 table.
CREATE TABLE IF not EXISTS redshift_lab.f_raw_1 (
  uuid			varchar(256),
  device_ts 		timestamp,
  device_id		int,
  device_temp		int,
  track_id		int,
  activity_type		varchar(128),
  load_time		int
);
```

```
--	Create d_ref_data_1 table.
CREATE TABLE IF NOT EXISTS redshift_lab.d_ref_data_1 (
  track_id		int,
  track_name	varchar(128),
  artist_name	varchar(128)
);
```

---

#### Chuyển đổi và load dữ liệu vào Redshift

**Tạo Glue Development Endpoint**

Ở bước này, chúng ta sẽ tạo Glue Dev Endpoint để tương tác với Glue ETL script sử dụng PySpark

+ Đi đến: Glue Development Endpoints [Nhấn vào đây](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=devEndpoints)
+ Nhấn **Add endpoint**
  + Development endpoints name: ```analyticsworkshopEndpoint2```
  + IAM role: **AnalyticsworkshopGlueRole**
  + Mở rộng **Security configuration.. parameters**
    + Data processing unit (DPUs): ```2``` (Điều này sẽ giảm chi phí chạy lab)
  + Tuỳ chọn thêm tags:
    + workshop: AnalyticsOnAWS
  + Nhấn **Next**

![Architect](/images/10/18.png?width=90pc)

  + Màn hình Networking:
    + Chọn **Choose a connection**
    + Chọn **analytics_workshop**
    + Nhấn **Next**

![Architect](/images/10/19.png?width=90pc)

  + Thêm SSH public key (TUỳ chọn):
    + Để mặc định
    + Ấn **Next**
  + Xem lại các cấu hình
    + Ấn **Finish**

Việc này sẽ mất tầm 10 phút để một Glue development endpoint mới được tạo ra

**Bạn cần phải đợi bước này hoàn thành trước khi qua bước tiếp theo**

---

#### Tạo SageMaker Notebooks (Jupyter) cho Glue Dev Endpoints

+ Đi đến: Notebooks console [Nhấn vào đây](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=notebooks)
+ Chọn tab **Sagemaker notebooks**
+ Nhấn **Create notebook**
  + Notebook name: ```AnalyticsworkshopRedshiftNotebook```
  + Attach to development endpoint: **analyticsworkshopEndpoint2**
  + Chọn **Choose an existing role**
  + IAM Role: **AnalyticsworkshopNotebookRole**
  + VPC (optional): Để trống
  + Encryption key (optional): Để trống
  + Tuỳ chọn thêm Tags:
    + workshop: AnalyticsOnAWS
  + Nhấn: **Create Notebook**

![Architect](/images/10/20.png?width=90pc)

Đợi vài phút để khởi tạo thành công

---

#### Chạy Jupyter Notebook

+ Tải xuống và lưu dưới máy file này: [https://intro-to-analytics-on-aws.workshop.aws/notebooks/analytics-workshop-redshift-notebook.ipynb](https://intro-to-analytics-on-aws.workshop.aws/notebooks/analytics-workshop-redshift-notebook.ipynb)
+ Đi đến: SageMaker Notebook
+ Bên trái chọn **Notebook**
+ Chọn **Open**

![Architect](/images/10/21.png?width=90pc)

+ Ở Sagemaker Jupyter Notebook:
  + Nhấn **Upload** (góc phải bên trên)
  + Tìm và tải lên **analytics-workshop-redshift-notebook.ipynb** mà bạn đã tải trước đó
  + Nhấn **Upload** để xác nhận

![Architect](/images/10/22.png?width=90pc)

  + Nhấn **analytics-workshop-redshift-notebook.ipynb** để mở notebook
  + Hãy chắc rằng '**Sparkmagic (PySpark)**' ở góc bên phải trên của notetbook, đây là tên của kernel mà Jupyter notebook sẽ sử dụng để chạy code của notebook
  + **Làm theo hướng dẫn tuần tự của notebook**
  + Hãy đọc và hiểu hướng dẫn, họ sẽ giải thích về độ quan trọng của GLue

---

#### Xác nhận - Chuyển đổi dữ liệu đã đi vào Redshift

Một khi ETL script đã chạy thành công, đi đến Redshift Query Editor [Nhấn vào đây](https://ap-southeast-1.console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1#query-editor)

Chạy câu query để kiểm trả số lượng record ở table của dữ liệu raw và reference

```
select count(1) from redshift_lab.f_raw_1;

select count(1) from redshift_lab.d_ref_data_1;
```

---

#### Một số câu query để thử

```
select 
  track_name, 
  artist_name, 
  count(1) frequency
from 
  redshift_lab.f_raw_1 fr
inner join 
  redshift_lab.d_ref_data_1 drf
on 
  fr.track_id = drf.track_id
where 
  activity_type = 'Running'
group by 
  track_name, artist_name
order by 
  frequency desc
limit 10;
```

![Architect](/images/10/23.png?width=90pc)

**Xin chúc mừng**

Bạn đã hoàn thành việc load dữ liệu từ S3 vào Redshift sử dụng Glue Serverless ETL

--- 

Nếu bạn muốn tìm hiểu thêm một chút về Redshiftm hãy làm theo các bước dưới của phần tuỳ chọn

{{% notice warning %}}
Hãy chắc rằng bạn sẽ làm phần dọn dẹp sau khi hoàn thành bài lab
{{% /notice %}}

---

#### Phần tuỳ chọn

Best Practice trên Redshift

Ở bước này, húng ta sẽ làm một số best practices của redshift bằng cách optimize nơi lưu trữ và hiệu năng của cluster dựa trên các câu lệnh query chạy trên Redshift cluster

**Mặc dù hầu hết các bước bạn sẽ thực hiện bên dưới đều được tự động hóa trong Redshift nhưng bạn sẽ tốt hơn nếu bạn luôn hiểu được các khái niệm chính và cách chúng hoạt động**

+ Sử dụng Redshift query editor để chạy các câu lệnh query ở bước tiếp theo:
  + Đi đến: Redshift Query Editor [Nhấn vào đây](https://ap-southeast-1.console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1#query-editor)

---

#### String column size

+ Kiểm tra độ dài tối đa của các cột dựa trên chuỗi.
  + Tất cả các cột dựa trên chuỗi không được phân bổ nhiều hơn độ chính xác cần thiết. Nó giúp giảm dung lượng lưu trữ trên cụm và cũng cải thiện hiệu suất truy vấn khi bạn sử dụng các cột này trong truy vấn bằng cách tiêu tốn ít bộ nhớ hơn.

```
select max(len(uuid)) as uuid_len, max(len(activity_type)) as activity_type_len from redshift_lab.f_raw_1;
      
select max(len(track_name)) as uuid_len, max(len(artist_name)) as activity_type_len from redshift_lab.d_ref_data_1;
```

+ Kết quả từ truy vấn trên sẽ được sử dụng để xác định độ chính xác mới cho các cột dựa trên chuỗi.
  + Nói chung, một bộ đệm được duy trì trong khi xác định độ chính xác của cột hoặc độ chính xác của cột có thể được cố định, nếu thuộc tính tiêu chuẩn của nó mà độ chính xác của cột được biết đến. Ví dụ: Tên miền Đủ điều kiện

---

#### Compression

Ở bước này, chúng ta sẽ phân tích table raw để compression

+ Kiểm tra thuật toán mã hóa thích hợp trên mỗi bảng để thực hiện nén.
  + Nén là một hoạt động ở cấp độ cột để giảm kích thước của dữ liệu khi nó được lưu trữ. Nén bảo toàn không gian lưu trữ và giảm kích thước của dữ liệu được đọc từ bộ lưu trữ, làm giảm số lượng I / O vào disk và do đó cải thiện hiệu suất truy vấn.

```
analyze compression redshift_lab.f_raw_1;
```

![Architect](/images/10/24.png?width=90pc)

+ Kết quả từ bảng trên cung cấp thông tin sau cho từng cột:

  + Cột
    + Encoding: Mã hóa được đề xuất dựa trên loại và giá trị độ chính xác của cột.
    + Est_reduction_pct: Phần trăm giảm ước tính nếu mã hóa được đề xuất được triển khai.

---


#### Distribution Style

+ Sử dụng phân phối dựa trên **KEY** cho bảng dữ kiện **f_raw_1**.
  + Vì hai bảng (**f_raw_1** và **d_ref_data_1**) cần được kết hợp trên cột **track_id**, nên đã chọn **track_id** làm khóa phân phối.
+ Sử dụng phân phối **ALL** cho bảng dimension - **d_ref_data_1**.

---

#### Sort Keys

Trong các truy vấn từ người tiêu dùng dữ liệu, thuộc tính **activity_type** đã được sử dụng để lọc euqality, do đó, thuộc tính này có thể được chọn làm cột sắp xếp.

---

#### New Table ĐL

Dựa trên tất cả các quan sát ở trên

  + Tạo cột mới sử dụng DDL của **f_raw_2** và **d_ref_data_2**


```
--fact table ddl
CREATE TABLE IF NOT EXISTS redshift_lab.f_raw_2 (
  uuid			varchar(40) ENCODE zstd,
  device_ts 		timestamp,
  device_id		int ENCODE az64,
  device_temp		int ENCODE az64,
  track_id		int ENCODE az64,
  activity_type		varchar(16) ENCODE bytedict sortkey,
  load_time		int ENCODE zstd
)
DISTKEY(track_id);
  
--dimension table ddl
CREATE TABLE IF NOT EXISTS redshift_lab.d_ref_data_2 (
  track_id		int,
  track_name		varchar(64),
  artist_name		varchar(64)
)
DISTSTYLE ALL;
```

---

#### Sao chép dữ liệu vào table mới

Khi mà tất cả dữ liệu đã có sẵ, sao chép dữ liệu từ table cũ sang table mới

```
--copy data from f_raw_1 to f_raw_2
insert into redshift_lab.f_raw_2 select * from redshift_lab.f_raw_1;
  
--copy data from d_ref_data_1 to d_ref_data_2
INSERT into redshift_lab.d_ref_data_2 select * from redshift_lab.d_ref_data_1; 
```

---

#### Run Vacuum and Analyze

Ở bước này chúng ta sẽ chạy vacuum và analyze trên table này

VACUUM: Sắp xếp lại các hàng và lấy lại không gian trong một bảng được chỉ định hoặc tất cả các bảng trong cơ sở dữ liệu hiện tại

ANALYZE: Cập nhật thống kê bảng để người lập kế hoạch truy vấn sử dụng

```
vacuum redshift_lab.f_raw_2;
analyze redshift_lab.f_raw_2;  
vacuum redshift_lab.d_ref_data_2;
analyze redshift_lab.d_ref_data_2;
```

---

#### Chạy Query

```--Top 10 tracks and corresponding artists for a particular activity type. 
select 
  track_name, 
  artist_name, 
  count(1) frequency
from 
  redshift_lab.f_raw_2 fr
inner join 
  redshift_lab.d_ref_data_2 drf
on 
  fr.track_id = drf.track_id
where 
  activity_type = 'Running'
group by 
  track_name, artist_name
order by 
  frequency desc
limit 10;
```

Bạn có thể so sánh phần nà với phần **Một số query để thử** và so sánh tốc độ như trên ảnh tốc độ từ 12s giờ chỉ còn 2s cho câu lệnh query này

![Architect](/images/10/25.png?width=90pc)

{{% notice warning %}}
Hãy chắc rằng bạn sẽ làm phần dọn dẹp sau khi hoàn thành bài lab
{{% /notice %}}
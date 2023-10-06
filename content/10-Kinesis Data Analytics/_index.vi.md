---
title : "Phân tích với Kinesis Data Analytics"
date :  "`r Sys.Date()`" 
weight : 10
chapter : false
pre : " <b> 10. </b> "
---

#### Phân tích với Kinesis Data Analytics

Trong phần trước, bạn đã khám phá cách phân tích dữ liệu bằng cách sử dụng Amazon Athena. Trong phần này, chúng ta sẽ thấy cách thực hiện phân tích thời gian thực của dữ liệu đang truyền bằng cách sử dụng Amazon Kinesis Data Analytics. Điều này có thể được thực hiện theo 2 cách, sử dụng Ứng dụng SQL cũ hoặc sử dụng Sổ ghi Studio mới được khuyến nghị. Trong buổi thực hành này, chúng ta sẽ sử dụng Sổ ghi Studio và tạo Ứng dụng Phân tích Kinesis dựa trên SQL.

#### Tạo IAM Role
Trong bước này, chúng ta sẽ điều hướng đến Bảng điều khiển IAM và tạo một role dịch vụ Amazon Kinesis Data Analytics mới. Điều này cho phép dịch vụ Amazon Kinesis Data Analytics truy cập vào Kinesis Data Streams cũng như AWS Glue Catalog table.

1. Đi đến Role AWS IAM
- Chọn  vào Create IAM Role
- Chọn dịch vụ Kinesis trong Use case từ menu thả xuống có tên Use cases for other AWS services:
- Chọn Kinesis Analytics
- Chọn  vào Next 

![Data Analytics on AWS](/images/9/0003.png?featherlight=false&width=90pc)

2. Tìm kiếm AWSGlueServiceRole
- Chọn hộp kiểm nhập của mục này
- Tìm kiếm AmazonKinesisFullAccess
- Chọn hộp kiểm nhập của mục này

LƯU Ý: Chúng tôi sử dụng quyền truy cập đầy đủ chỉ cho mục đích thực hành. Hãy cấp quyền truy cập cần thiết nếu bạn sử dụng Role này trong môi trường sản xuất.



![Data Analytics on AWS](/images/9/0004.png?featherlight=false&width=90pc)


3. Chọn  vào Next
- Nhập tên Role: AnalyticsworkshopKinesisAnalyticsRole
- Đảm bảo chỉ có hai policy được gắn kết vào Role này (AWSGlueServiceRole, AmazonKinesisFullAccess)
- Tùy chọn thêm Tag, ví dụ: workshop: AnalyticsOnAWS
- Chọn  vào Create IAM Role

![Data Analytics on AWS](/images/9/0005.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/9/0006.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/9/0007.png?featherlight=false&width=90pc)

#### Tạo Kinesis  Data Stream 

Kinesis Data Generator là một ứng dụng giúp việc gửi dữ liệu kiểm thử tới luồng Kinesis của Amazon hoặc luồng chuyển phân phối Firehose của Amazon Kinesis trở nên đơn giản. Chúng ta sẽ tạo luồng dữ liệu Kinesis để tiếp nhận dữ liệu từ Kinesis Data Generator. Sổ ghi chú Ứng dụng Kinesis của chúng ta sẽ đọc dữ liệu đang truyền từ luồng dữ liệu Kinesis này.

1. Truy cập vào dịch vụ AWS Kinesis
Chọn  vào Create Data Stream


![Data Analytics on AWS](/images/9/0008.png?featherlight=false&width=90pc)

2. Nhập tên luồng dữ liệu: analytics-workshop-data-stream
- Data Stream capacity:
- Choose Capacity Mode: Provisioned
- Set Provisioned Shards: 2

![Data Analytics on AWS](/images/9/0009.png?featherlight=false&width=90pc)

3. THÔNG TIN: Một shard là một nhóm các bản ghi dữ liệu đặc biệt được xác định trong luồng dữ liệu Kinesis. Một shard hỗ trợ 1 MB/giây và 1.000 bản ghi mỗi giây cho việc ghi và 2 MB/giây cho việc đọc. Vì vậy, 2 shard được cấp phát ở đây có thể hỗ trợ 2 MB/giây và 2.000 bản ghi mỗi giây cho việc ghi và 4 MB/giây cho việc đọc.

- Cuộn xuống dưới cùng và Chọn  vào Create Data Stream

![Data Analytics on AWS](/images/9/00010.png?featherlight=false&width=90pc)

#### Tạo Glue Catalog Table
Kinesis Application Notebook của chúng tôi sẽ lấy thông tin về nguồn dữ liệu từ AWS Glue. Khi bạn tạo Studio notebook, bạn chỉ định AWS Glue database chứa thông tin kết nối của bạn. Khi truy cập vào nguồn dữ liệu của bạn, bạn chỉ định các bảng AWS Glue được chứa trong cơ sở dữ liệu. 

1. Từ thanh bên trái, đi đến Database và Chọn  vào cơ sở dữ liệu đã tạo trước đó analyticsworkshopdb của chúng tôi

- Chọn  vào Tables in analyticsworkshopdb

- Chọn  vào menu thả xuống  Add tables và sau đó chọn Add table manually


![Data Analytics on AWS](/images/9/00011.png?featherlight=false&width=90pc)

2. Trong Table Properties

- Nhập Table Name: raw_stream


![Data Analytics on AWS](/images/9/00012.png?featherlight=false&width=90pc)

3. Trong Data store:

- Chọn loại nguồn: Kinesis
- Bỏ qua Select a kinesis data stream. (Stream in my account được chọn mặc định)
- Region US East (N. Virginia) us-east-1
- Kinesis stream name analytics-workshop-data-stream
- Bỏ qua kích thước mẫu
- Trong Data format:
- Classification: JSON
- Sau đó, Chọn  vào Next

![Data Analytics on AWS](/images/9/00013.png?featherlight=false&width=90pc)

4. Trong Schema: Chọn  vàoEdit Schema as JSON và chèn đoạn văn bản JSON sau đây.

![Data Analytics on AWS](/images/9/00014.png?featherlight=false&width=90pc)

```
[
  {
    "Name": "uuid",
    "Type": "string",
    "Comment": ""
  },
  {
    "Name": "device_ts",
    "Type": "timestamp",
    "Comment": ""
  },
  {
    "Name": "device_id",
    "Type": "int",
    "Comment": ""
  },
  {
    "Name": "device_temp",
    "Type": "int",
    "Comment": ""
  },
  {
    "Name": "track_id",
    "Type": "int",
    "Comment": ""
  },
  {
    "Name": "activity_type",
    "Type": "string",
    "Comment": ""
  }
]

```

![Data Analytics on AWS](/images/9/00015.png?featherlight=false&width=90pc)

5. Trong Schema: Sau đó, Chọn  vào Next


![Data Analytics on AWS](/images/9/00016.png?featherlight=false&width=90pc)

6. Trong  Partition:  Bỏ qua phần này và Chọn  vào Next
INFO: Chỉ số phân vùng là một chỉ số cho các khóa phân vùng được xác định trong bảng. Điều này hữu ích để truy xuất một phần con của các phân vùng thay vì tải tất cả các phân vùng. Tìm thông tin chi tiết tại đây.

- Chọn  vào Next

- Kiểm tra rằng tất cả thông tin đều chính xác, sau đó Chọn  vào Create


![Data Analytics on AWS](/images/9/00017.png?featherlight=false&width=90pc)

7. Xác minh rằng bảng Glue mới raw_stream đã được tạo đúng. Làm mới danh sách bảng nếu nó chưa hiển thị.

- Chọn  vào bảng mới tạo raw_stream

- Chọn  vào  Actions và Chọn  vào Edit table

![Data Analytics on AWS](/images/9/00018.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/9/00019.png?featherlight=false&width=90pc)

8. Dưới Table properties, thêm thuộc tính mới:
- Key: kinesisanalytics.proctime
- Value: proctime
- INFO: Các thuộc tính giá trị khóa này cho biết thời gian đã xử lý dữ liệu của Kinesis Analytics

![Data Analytics on AWS](/images/9/00020.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/9/00021.png?featherlight=false&width=90pc)

#### Tạo Analytics Streaming Application Studio Notebook

Bây giờ chúng ta hãy tạo Kinesis Analytics Streaming Application Studio Notebook của chúng ta trong Kinesis Analytics Studio. Kinesis Analytics Streaming Application Studio Notebook này có thể xử lý dữ liệu luồng từ Kinesis Data Stream và chúng ta có thể viết các truy vấn phân tích SQL để lấy thông tin thời gian thực như số lượng hoạt động hiện tại hoặc nhiệt độ thiết bị.

1. Chuyển đến Studio
- Chọn  vào Create Studio notebook

![Data Analytics on AWS](/images/9/00022.png?featherlight=false&width=90pc)

2. Chọn Create with custom settings
- Nhập Studio notebook name: AnalyticsWorkshop-KDANotebook
- Nhập Runtime: Apache Flink 1.11, Apache Zeppelin 0.9
- Chọn  vào Next

![Data Analytics on AWS](/images/9/00023.png?featherlight=false&width=90pc)

3. Trong IAM role
- Chọn Choose from IAM roles that Kinesis Data Analytics can assume
- Chọn Role dịch vụ đã được tạo trước đó của chúng ta: AnalyticsworkshopKinesisAnalyticsRole
- Trong AWS Glue database, chọn: analyticsworkshopdb
- Chọn  vào Next

![Data Analytics on AWS](/images/9/00024.png?featherlight=false&width=90pc)

4. Trong Configurations
- Parallelism: 4
- Parallelism per KPU: 1


![Data Analytics on AWS](/images/9/00025.png?featherlight=false&width=90pc)

5. Không bật Turn on Logging (Bỏ chọn ô kiểm Bật ghi nhật ký)
- INFO: Ghi nhật ký hữu ích để hiểu lỗi khi ứng dụng của bạn gặp sự cố. Để thực hiện điều này, cần thêm quyền CLoudwatchFullAccess và CloudwatchLogFullAccess cho role dịch vụ. Chúng ta sẽ bỏ qua phần này vì không cần thiết trong bài thực hành này.

- Bỏ qua tất cả mọi thứ và di chuyển xuống dưới cùng

![Data Analytics on AWS](/images/9/00026.png?featherlight=false&width=90pc)

6. Trong Tags:
- Tùy chọn thêm các Tag, ví dụ:workshop: AnalyticsOnAWS
- Chọn  vào Next

![Data Analytics on AWS](/images/9/00027.png?featherlight=false&width=90pc)

7. Trong Review và create
- Xác nhận rằng tất cả các giá trị đều đúng
- Chọn  vào Create Studio notebook

![Data Analytics on AWS](/images/9/00028.png?featherlight=false&width=90pc)

8. Chạy Kinesis Analytics Studio Notebook
- Bây giờ chúng ta đã tạo Notebook, chúng ta có thể chạy nó và thử thực thi một số truy vấn SQL.

- Xem danh sách các Notebook trong tab Studio và Chọn  vào Notebook mới được tạo AnalyticsWorkshop-KDANotebook của chúng ta.

- Chọn  vào Run

- Chờ cho đến khi Status chuyển sang Running mode. (Việc này sẽ mất khoảng 5-7 phút)

![Data Analytics on AWS](/images/9/00029.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/9/00030.png?featherlight=false&width=90pc)

9. Chọn  vào Open in Apache Zeppelin ở góc trên bên phải để mở Zeppelin Notebook.

- Chọn  vào Create new note và đặt tên cho ghi chú là AnalyticsWorkshop-ZeppelinNote.

- Dán câu truy vấn SQL này.

```
%flink.ssql(type=update)

SELECT * FROM raw_stream;

```

![Data Analytics on AWS](/images/9/00031.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/9/00032.png?featherlight=false&width=90pc)

10. Câu truy vấn SQL này sẽ liệt kê tất cả dữ liệu streaming từ Kinesis Data Generator của chúng ta.
type=update là một trình thông dịch Flink cho cú pháp ghi chú Zeppelin. Trong chế độ update, đầu ra của ghi chú sẽ được cập nhật liên tục với kết quả mới.

```
%flink.ssql(type=update)

SELECT activity_type, count(*) as activity_cnt FROM raw_stream group by activity_type;

```

- Câu truy vấn SQL này sẽ đếm số lượng hoạt động đang được thực hiện.
- Khi tất cả các truy vấn được dán vào, Chọn  vào nút Play ở góc phải trên của đoạn văn.

![Data Analytics on AWS](/images/9/00033.png?featherlight=false&width=90pc)

#### Generate Dummy Data to Kinesis Data Stream

Để hiển thị dữ liệu từ các truy vấn chạy trong Analytics Streaming notebook, chúng ta phải gửi dữ liệu gốc từ Kinesis Data Generator của chúng ta.

1. Truy cập vào KinesisDataGeneratorURL. Bạn có thể tìm thấy nó trong tab Output của stack Cloudformation. 
- Đăng nhập bằng tên người dùng và mật khẩu của bạn
- Điền thông tin như sau:
- Khu vực (Region): us-east-1
- Luồng/luồng giao hàng (Stream/delivery stream): analytics-workshop-data-stream (ĐỪNG chọn analytics-workshop-stream mà bạn có thể đã tạo trong mô-đun "Ingest and Store")
- Đảm bảo Records per second (Số bản ghi mỗi giây) là Constant.
- Giá trị cho Records per second (Số bản ghi mỗi giây): 100 (ĐỪNG thay đổi số này.)
- Đảm bảo Compress Records (Nén bản ghi) không được chọn.
- Mẫu bản ghi (Template 1): Trong khu vực văn bản lớn, chèn mẫu json sau:

```
{
  "uuid": "{{random.uuid}}",
  "device_ts": "{{date.utc("YYYY-MM-DD HH:mm:ss.SSS")}}",
  "device_id": {{random.number(50)}},
  "device_temp": {{random.weightedArrayElement(
    {"weights":[0.30, 0.30, 0.20, 0.20],"data":[32, 34, 28, 40]}
  )}},
  "track_id": {{random.number(30)}},  
  "activity_type": {{random.weightedArrayElement(
        {
            "weights": [0.1, 0.2, 0.2, 0.3, 0.2],
            "data": ["\"Running\"", "\"Working\"", "\"Walking\"", "\"Traveling\"", "\"Sitting\""]
        }
    )}}
}

```

![Data Analytics on AWS](/images/9/00034.png?featherlight=false&width=90pc)

2. Sau đó, Chọn  vào  Send Data.
- CHÚ Ý: KHÔNG TẠM DỪNG sau khi Chọn  vào  Send Data vì điều này là cần thiết để có luồng liên tục dữ liệu để phân tích trong Zeppelin notebook.
- Quay trở lại Zeppelin notebook. của chúng ta. Chờ vài phút, kết quả sẽ được hiển thị.

![Data Analytics on AWS](/images/9/00035.png?featherlight=false&width=90pc)


Trong module này, bạn đã tạo một Kinesis Data Stream để nhận dữ liệu luồng từ Kinesis Data Generator, một bảng Glue lưu trữ thông tin về lược đồ và dữ liệu của Kinesis Data Stream, và một ứng dụng Kinesis Analytics Studio Notebook đọc và phân tích dữ liệu luồng.

Next, chúng ta sẽ tìm hiểu cách xây dựng các biểu đồ/ bảng điều khiển bằng cách sử dụng Amazon Quicksight.
---
title : "Serve with Lambda"
date: 2024-01-01
weight : 12
chapter : false
pre : " <b> 12. </b> "
---

#### Serve with Lambda
Trong module này, chúng ta sẽ tạo một Lambda Function với một ví dụ sử dụng cụ thể. Lambda function mà chúng ta sẽ viết sẽ chứa mã cho Athena để truy vấn và lấy 5 Bài hát phổ biến nhất theo số lượt truy cập từ dữ liệu đã được xử lý trong S3.


1.  Tạo một Lambda Function
- Đi đến: Bảng điều khiển Lambda
- Chú ý: Đảm bảo đã chọn Region là US East (N. Virginia) tức là us-east-1
- Chọn  vào Create function (nếu bạn đang sử dụng Lambda lần đầu, thì có thể bạn phải Chọn  vào Bắt đầu để tiếp tục)


![Data Analytics on AWS](/images/11/0001.png?featherlight=false&width=90pc)

2. Chọn Author from scratch
- Dưới  Basic Information:
- Đặt unction name là Analyticsworkshop_top5Songs
- Chọn Runtime là Python 3.8
- Mở rộng Choose or create an execution role under Permissions, đảm bảo đã chọn Create a new role của Lambda.
- Chọn  vào Create Function

![Data Analytics on AWS](/images/11/0002.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/0003.png?featherlight=false&width=90pc)

#### Author Lambda Function

Trong phần này, chúng tôi sẽ cung cấp mã cho hàm lambda mà chúng tôi vừa tạo. Chúng tôi sẽ sử dụng boto3 để truy cập client Athena.

Boto là Software Development Kit (SDK) của Amazon Web Services (AWS) cho Python. Nó cho phép các nhà phát triển Python tạo, cấu hình và quản lý các dịch vụ AWS, như EC2 và S3. Boto cung cấp một API dễ sử dụng, hướng đối tượng, cũng như truy cập cấp thấp vào các dịch vụ AWS. Đọc thêm về Boto tại đây - https://boto3.amazonaws.com/v1/documentation/api/latest/index.html?id=docs_gateway

Đọc thêm về các phương thức API Athena của Boto3 tại đây - https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/athena.html

![Data Analytics on AWS](/images/11/0004.png?featherlight=false&width=90pc)

3. Phần sau là đoạn mã Python để thay thế vào phần mã hiện tại trong tệp lambda_function.py. Hãy cuộn xuống phần Mã chức năng và thay thế mã hiện tại bằng đoạn mã Python dưới đây:

```
import boto3
import time
import os

# Environment Variables
DATABASE = os.environ['DATABASE']
TABLE = os.environ['TABLE']
# Top X Constant
TOPX = 5
# S3 Constant
S3_OUTPUT = f's3://{os.environ["BUCKET_NAME"]}/query_results/'
# Number of Retries
RETRY_COUNT = 10

def lambda_handler(event, context):
    client = boto3.client('athena')
    # query variable with two environment variables and a constant
    query = f"""
        SELECT track_name as \"Track Name\", 
                artist_name as \"Artist Name\",
                count(1) as \"Hits\" 
        FROM {DATABASE}.{TABLE} 
        GROUP BY 1,2 
        ORDER BY 3 DESC
        LIMIT {TOPX};
    """
    response = client.start_query_execution(
        QueryString=query,
        QueryExecutionContext={ 'Database': DATABASE },
        ResultConfiguration={'OutputLocation': S3_OUTPUT}
    )
    query_execution_id = response['QueryExecutionId']
    # Get Execution Status
    for i in range(0, RETRY_COUNT):
        # Get Query Execution
        query_status = client.get_query_execution(
            QueryExecutionId=query_execution_id
        )
        exec_status = query_status['QueryExecution']['Status']['State']
        if exec_status == 'SUCCEEDED':
            print(f'Status: {exec_status}')
            break
        elif exec_status == 'FAILED':
            raise Exception(f'STATUS: {exec_status}')
        else:
            print(f'STATUS: {exec_status}')
            time.sleep(i)
    else:
        client.stop_query_execution(QueryExecutionId=query_execution_id)
        raise Exception('TIME OVER')
    # Get Query Results
    result = client.get_query_results(QueryExecutionId=query_execution_id)
    print(result['ResultSet']['Rows'])
    # Function can return results to your application or service
    # return result['ResultSet']['Rows']

```

![Data Analytics on AWS](/images/11/0005.png?featherlight=false&width=90pc)


![Data Analytics on AWS](/images/11/0006.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/0007.png?featherlight=false&width=90pc)


4.  Environment Variables
- Environment Variables cho các hàm Lambda cho phép bạn truyền động các thiết lập vào mã hàm và thư viện của bạn mà không cần thay đổi mã của bạn. Đọc thêm về Environment Variables Lambda tại đây - https://docs.aws.amazon.com/lambda/latest/dg/env_variables.html

- Cuộn xuống phần Environment Variables và thêm ba Environment Variables sau đây.
- Key: DATABASE, Value: analyticsworkshopdb
- Key: TABLE, Value: processed_data
- Key: BUCKET_NAME, Value: yourname-analytics-workshop-bucket
- Để Memory (MB) mặc định là 128 MB
- Thay đổi Timeout  thành 10 giây.
- Tùy chọn thêm Tag, ví dụ: workshop: AnalyticsOnAWS
- Chọn  vào Save

![Data Analytics on AWS](/images/11/0008.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/0009.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00010.png?featherlight=false&width=90pc)


5. Execution Role
- Chọn Permissions Tab phía trên:
- Chọn  vào liên kết Role Name dưới  Execution Role  để mở IAM Console trong một tab mới.
- Chọn  vào Add permissions và Chọn  vào Attach policies
- Thêm hai policies  sau (tìm trong hộp lọc, chọn và Chọn  Attach policy):
- AmazonS3FullAccess
- AmazonAthenaFullAccess
- Sau khi các policy này được gắn vào role, đóng tab này.

![Data Analytics on AWS](/images/11/00011.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00012.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00013.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00014.png?featherlight=false&width=90pc)

6. Cấu hình Test Event
- Chức năng của chúng ta đã sẵn sàng để được kiểm tra. Trước tiên, triển khai chức năng bằng cách Chọn  vào Deploy dưới phần Function code.
- Next, hãy cấu hình một sự kiện kiểm tra giả để xem kết quả thực thi của chức năng lambda mới được tạo.
- Chọn  vào Test ở góc trên bên phải của bảng điều khiển lambda.
- Một cửa sổ mới sẽ hiện ra để chúng ta cấu hình sự kiện kiểm tra.
- Mặc định là Create new test event.
- Event name: Test
- Template: Hello World
- Để mọi thứ như cũ
- Chọn  vào Save
- Chọn  vào  Test một lần nữa
- Bạn nên có thể nhìn thấy đầu ra theo định dạng json dưới phần Execution Result .

![Data Analytics on AWS](/images/11/00015.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00016.png?featherlight=false&width=90pc)

7. Xác minh thông qua Athena
- Hãy xác minh kết quả thông qua Athena
- Truy cập: Athena Console 
- Trên bảng điều khiển bên trái, chọn analyticsworkshopdb từ menu thả xuống
- Chạy truy vấn sau đây:

```
SELECT track_name as "Track Name",
    artist_name as "Artist Name",
    count(1) as "Hits" 
FROM analyticsworkshopdb.processed_data 
GROUP BY 1,2 
ORDER BY 3 DESC 
LIMIT 5;

```

![Data Analytics on AWS](/images/11/00017.png?featherlight=false&width=90pc)

So sánh kết quả của truy vấn này với kết quả của hàm lambda; chúng nên giống nhau.

TUYỆT VỜI!

Bây giờ bạn đã tạo ra một hàm lambda từ đầu và đã kiểm tra nó.

Module Next sẽ đề cập đến chủ đề cuối cùng về xây dựng Data Warehouse trên Amazon Redshift.
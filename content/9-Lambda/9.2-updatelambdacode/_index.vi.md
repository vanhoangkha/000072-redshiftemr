+++
title = "Viết code Lambda Function"
date = 2020
weight = 2
chapter = false
pre = "<b>9.2 </b>"
+++

#### Viết code Lambda Function

Ở phần này, chúng ta sẽ code cho lambda function chúng ta vừa tạo. Chúng ta sẽ sử dụng ```boto3``` để truy cập đến Athena.

{{% notice note %}}
Boto là SDK của Dịch vụ Web Amazon (AWS) dành cho Python. Nó cho phép các nhà phát triển Python tạo, định cấu hình và quản lý các dịch vụ AWS, chẳng hạn như EC2 và S3. Boto cung cấp một API hướng đối tượng, dễ sử dụng, cũng như quyền truy cập cấp thấp vào các dịch vụ AWS. Đọc thêm về Boto tại đây [https://boto3.amazonaws.com/v1/documentation/api/latest/index.html?id=docs_gateway](https://boto3.amazonaws.com/v1/documentation/api/latest/index.html?id=docs_gateway)
{{% /notice %}}



1. Kéo xuống đến phần Function Code và thay thế code có sẵn trong **lambda_function.py** với đoạn python code dưới đây

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

2. Cấu hình biến môi trường, click vào tab **Configuration**.

{{% notice note %}}
Các biến môi trường cho các hàm Lambda cho phép bạn chuyển động cài đặt vào mã hàm và thư viện của bạn mà không cần thực hiện thay đổi đối với mã của bạn. Đọc thêm về Biến môi trường Lambda tại đây [https://docs.aws.amazon.com/lambda/latest/dg/env_variables.html](https://docs.aws.amazon.com/lambda/latest/dg/env_variables.html)
{{% /notice %}}

  + Click **Environment variables**.
  + Click **Edit**.

![Architect](/images/9/2.png?width=90pc)

3. Thêm 3 **Environment variables** dưới đây
  + Key: ```DATABASE```, Value: ```analyticsworkshopdb```.
  + Key: ```TABLE```, Value: ```processed_data```.
  + Key: ```BUCKET_NAME```, ```Value: yourname-analytics-workshop-bucket```.
  + Click **Save**.
![Architect](/images/9/3.png?width=90pc)

4. Click **General Configuration**.
  + Click **Edit**.
  + Để **Memory (MB)** như mặc định là 128 MB.
  + Đổi **Timeout** thành 10 seconds.
  + Nhấn **Save**.

![Architect](/images/9/11.png?width=90pc)

---

5. Click **Permissions**.
  + Nhấn link Role Name để mở IAM Console ở tab mới.

![Architect](/images/9/4.png?width=90pc)

6. Nhấn **Attach policies**

![Architect](/images/9/5.png?width=90pc)

7. Thêm 2 policies như dưới đây:
  + ```AmazonS3FullAccess```
  + ```AmazonAthenaFullAccess```

![Architect](/images/9/6.png?width=90pc)

Khi các policies đã được gắn vào, chúng ta có thể tắt tab này và quay trở lại giao diện của dịch vụ Lambda.

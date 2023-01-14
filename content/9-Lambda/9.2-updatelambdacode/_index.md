+++
title = "Writing Lambda Function Code"
date = 2020
weight = 2
chapter = false
pre = "<b>9.2 </b>"
+++

#### Write Lambda Function code

In this part, we will code for the lambda function we just created. We will use ```boto3``` to access Athena.

{{% notice note %}}
Boto is the Amazon Web Services (AWS) SDK for Python. It allows Python developers to create, configure, and manage AWS services, such as EC2 and S3. Boto provides an easy-to-use, object-oriented API, as well as low-level access to AWS services. Read more about Boto here [https://boto3.amazonaws.com/v1/documentation/api/latest/index.html?id=docs_gateway](https://boto3.amazonaws.com/v1/documentation/api/ latest/index.html?id=docs_gateway)
{{% /notice %}}



1. Scroll down to the Function Code section and replace the code available in **lambda_function.py** with the python code below.

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

![Data Analysis on AWS](/images/9/4.png?featherlight=false&width=90pc)

2. To configure the environment variable, click the **Configuration** tab.

{{% notice note %}}
Environment variables for Lambda functions allow you to move settings into your function code and libraries without making changes to your code. Read more about Lambda Environment Variables here [https://docs.aws.amazon.com/lambda/latest/dg/env_variables.html](https://docs.aws.amazon.com/lambda/latest/dg /env_variables.html)
{{% /notice %}}

  + Click **Environment variables**.
  + Click **Edit**.

![Data Analysis on AWS](/images/9/5.png?featherlight=false&width=90pc)


3. Add 3 **Environment variables** below
  + Key: ```DATABASE```, Value: ```analyticsworkshopdb```.
  + Key: ```TABLE```, Value: ```processed_data```.
  + Key: ```BUCKET_NAME```, ```Value: yourname-analytics-workshop-bucket```.
  + Click **Save**.


![Data Analysis on AWS](/images/9/6.png?featherlight=false&width=90pc)

4. Click **General Configuration**.
  + Click **Edit**.
  + Leave **Memory (MB)** as default 128 MB.
  + Change **Timeout** to 10 seconds.
  + Click **Save**.

![Data Analysis on AWS](/images/9/8.png?featherlight=false&width=90pc)

---

5. Click **Permissions**.
  + Click the Role Name link to open the IAM Console in a new tab.

![Data Analysis on AWS](/images/9/9.png?featherlight=false&width=90pc)

6. Click **Attach policies**

![Data Analysis on AWS](/images/9/10.png?featherlight=false&width=90pc)

7. Add 2 policies as below:
  + ```AmazonS3FullAccess````
  + ```AmazonAthenaFullAccess```

![Data Analysis on AWS](/images/9/11.png?featherlight=false&width=90pc)

Once the policies have been attached, we can close this tab and return to the interface of the Lambda service.
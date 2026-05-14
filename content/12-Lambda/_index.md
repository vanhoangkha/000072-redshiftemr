---
title : "Serve with Lambda"
date: 2024-01-01
weight : 12
chapter : false
pre : " <b> 12. </b> "
---

#### Serve with Lambda
In this module, we will create a Lambda Function with a specific usage example. The lambda function that we are going to write will contain code for Athena to query and get the 5 Most Popular Songs by hits from the data processed in S3.


1. Create a Lambda Function
- Go to: Lambda Dashboard
- Note: Make sure Region is selected as US East (N. Virginia) ie us-east-1
- Select Create function (if you are using Lambda for the first time, you may have to Select Start to continue)


![Data Analytics on AWS](/images/11/0001.png?featherlight=false&width=90pc)

2. Select Author from scratch
- Under Basic Information:
- Set unction name as Analyticsworkshop_top5Songs
- Select Runtime as Python 3.8
- Expand Choose or create an execution role under Permissions, make sure Create a new role of Lambda is selected.
- Select Create Function

![Data Analytics on AWS](/images/11/0002.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/0003.png?featherlight=false&width=90pc)

#### Author Lambda Function

In this section, we will provide the code for the lambda function we just created. We will use boto3 to access the Athena client.

Boto is the Amazon Web Services (AWS) Software Development Kit (SDK) for Python. It allows Python developers to create, configure, and manage AWS services, such as EC2 and S3. Boto provides an easy-to-use, object-oriented API, as well as low-level access to AWS services. Read more about Boto here - https://boto3.amazonaws.com/v1/documentation/api/latest/index.html?id=docs_gateway

Read more about Boto3 Athena API methods here - https://boto3.amazonaws.com/v1/documentation/api/latest/reference/services/athena.html

![Data Analytics on AWS](/images/11/0004.png?featherlight=false&width=90pc)

3. The following is the Python code to replace the existing code in the lambda_function.py file. Scroll down to the Functional Code section and replace the existing code with the Python code below:


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

4. Environment Variables
- Environment Variables for Lambda functions allow you to pass settings into your function code and libraries without changing your code. Read more about Environment Variables Lambda here - https://docs.aws.amazon.com/lambda/latest/dg/env_variables.html

Scroll down to the Environment Variables section and add the following three Environment Variables.
- Key: DATABASE, Value: analyticsworkshopdb
- Key: TABLE, Value: processed_data
- Key: BUCKET_NAME, Value: yourname-analytics-workshop-bucket
- Leave the default Memory (MB) to 128 MB
- Change Timeout to 10 seconds.
- Option to add Tag, for example: workshop: AnalyticsOnAWS
- Select Save

![Data Analytics on AWS](/images/11/0008.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/0009.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00010.png?featherlight=false&width=90pc)


5. Execution Role
- Select Permissions Tab above:
- Click on the Role Name link under Execution Role to open the IAM Console in a new tab.
- Select Add permissions and Select Attach policies
- Add the following two policies (find in the filter box, select and Select Attach policy):
- AmazonS3FullAccess
- AmazonAthenaFullAccess
- After these policies are attached to the role, close this tab.

![Data Analytics on AWS](/images/11/00011.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00012.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00013.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00014.png?featherlight=false&width=90pc)

6. Test Event Configuration
- Our functionality is ready to be tested. First, deploy the function by selecting Deploy under the Function code section.
- Next, configure a mock test event to see the execution result of the newly created lambda function.
- Select Test in the upper right corner of the lambda console.
- A new window will appear for us to configure the test event.
- Default is Create new test event.
- Event name: Test
- Template: Hello World
- Leave everything as it is
- Select Save
- Select Test again
- You should be able to see the output in json format under Execution Result section.

![Data Analytics on AWS](/images/11/00015.png?featherlight=false&width=90pc)

![Data Analytics on AWS](/images/11/00016.png?featherlight=false&width=90pc)

7. Verification via Athena
- Please verify the result through Athena
- Access: Athena Console
- On the left panel, select analyticsworkshopdb from the drop-down menu
- Run the following query:


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

Compare the results of this query with the results of the lambda function; they should be the same.

GREAT!

You have now created a lambda function from scratch and tested it.

The Next module will cover the final topic of building Data Warehouse on Amazon Redshift.
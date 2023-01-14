+++
title = "Create S3 Gateway Endpoint"
date = 2021
weight = 3
chapter = false
pre = "<b>10.3 </b>"
+++


#### Create S3 Gateway Endpoint

In this step, we will create S3 Gateway Endpoint so that Redshift cluster can communicate with S3 using private IP.

1. Go to [VPC service admin interface](https://console.aws.amazon.com/vpc/home?region=ap-southeast-1#Endpoints:sort=vpcEndpointId).
  + Click **Create Endpoint**.

![Data Analysis on AWS](/images/10/13.png?featherlight=false&width=90pc)

2. Select **AWS Service** under **Service category**.

![Data Analysis on AWS](/images/10/14.png?featherlight=false&width=90pc)

  + Under **Service name** in the search box, find **S3** and Click enter.
  + **com.amazonaws.ap-southeast-1.s3** will appear below the search results. Select this option.
  + In the **VPC** section, select the default VPC. This is also the VPC used when configuring the redshift cluster.
  + If more than 1 VPC is listed, check Redshift's VPC to avoid confusion.
    + Go to: Redshift console [Click here](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1).
    + Click **redshift-cluster-1**.
    + Click the **Properties** tab.
    + Scroll down and check the **Network and security** section to find the name of the VPC.
  + Once you have checked the VPC, go to the **Configure route tables** section.
  Select the list route table (it should be the main route table). You can confirm by checking **Yes** under the **Main** column.


![Data Analysis on AWS](/images/10/15.png?featherlight=false&width=90pc)

3. Leave **Policy** as default (**Full Access**)

![Data Analysis on AWS](/images/10/16.png?featherlight=false&width=90pc)


{{% notice note %}}
**com.amazonaws.ap-southeast-1.s3** the id is listed again in **Configure route tables**. It should start with pl-[some number]
{{% /notice %}}


4. Click **Create endpoint**.

![Data Analysis on AWS](/images/10/17.png?featherlight=false&width=90pc)

5. This will take a few seconds to initialize. Once ready, you will see **Status** as **Available**.

![Data Analysis on AWS](/images/10/18.png?featherlight=false&width=90pc)
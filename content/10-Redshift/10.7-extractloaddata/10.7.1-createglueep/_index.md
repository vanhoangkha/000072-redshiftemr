+++
title = "Create Glue Dev Endpoint"
date = 2021
weight = 1
chapter = false
pre = "<b>10.7.1 </b>"
+++

#### Create Glue Development Endpoint

In this step, we will create Glue Dev Endpoint to interact with Glue ETL script using PySpark.

1. Go to the [Development Endpoints interface of the Glue service](https://console.aws.amazon.com/glue/home?region=ap-southeast-1#etl:tab=devEndpoints).
  + Click **Add endpoint**.

![Data Analysis on AWS](/images/10/36.png?featherlight=false&width=90pc)

2. Development endpoints name: ```analyticsworkshopEndpoint2```.
  + IAM role: **AnalyticsworkshopGlueRole**.
  + Expand **Security configuration.. parameters**.
    + Data processing units (DPUs): ```2``` (This will reduce the cost of running the lab).

![Data Analysis on AWS](/images/10/37.png?featherlight=false&width=90pc)

3. Optionally add tags:.
    + workshop: AnalyticsOnAWS.
  + Click **Next**.

![Data Analysis on AWS](/images/10/38.png?featherlight=false&width=90pc)

4. At the **Networking** page:
    + Select **Choose a connection**.
    + Select **analytics_workshop**.
    + Click **Next**.

![Data Analysis on AWS](/images/10/39.png?featherlight=false&width=90pc)

5. At the **SSH public key** page.
  + Add SSH public key (Optional):
    + Leave default.
    + Click **Next**.

![Data Analysis on AWS](/images/10/40.png?featherlight=false&width=90pc)

4. At **Review** page
  + Review the configuration.
  + Click **Finish**.

![Data Analysis on AWS](/images/10/41.png?featherlight=false&width=90pc)

5. This will take about 10 minutes for a new Glue development endpoint to be created.

![Data Analysis on AWS](/images/10/42.png?featherlight=false&width=90pc)

6. Complete creation of the Glue development endpoint.

![Data Analysis on AWS](/images/10/43.png?featherlight=false&width=90pc)

**You need to wait for this step to complete before proceeding to the next step**.
+++
title = "Create Redshift connection"
date = 2021
weight = 5
chapter = false
pre = "<b>10.5 </b>"
+++

#### Create Redshift connection via Glue connection.

In this step, we will create a Redshift Connection via Glue connection. You will use the Redshift connection in the Development Endpoint to create the connection to Redshift.

1. Go to [Glue service administration interface](https://us-east-1.console.aws.amazon.com/glue/home?region=ap-southeast-1#catalog:tab=connections ).
  + Click **Add Connection**.

![Data Analysis on AWS](/images/10/23.png?featherlight=false&width=90pc)

2. Let **Connection name** be ```analytics_workshop```.
    + Select **Connection type** as **Amazon Redshift**.
    + Click **Next**.

![Data Analysis on AWS](/images/10/24.png?featherlight=false&width=90pc)

3. Establish connection to data store:
    + Select **Cluster** as **redshift-cluster-1**.
    + Database name and Username will be automatically created as dev and admin.
    + **Password**: Enter the password you provided when creating the Redshift cluster.
    + Click **Next**.
  

![Data Analysis on AWS](/images/10/25.png?featherlight=false&width=90pc)

4. Then review the connection details and Click **Finish**.

![Data Analysis on AWS](/images/10/26.png?featherlight=false&width=90pc)

5. We will test this connection:
    + Select connection **analytics_workshop**.
    + Click **Test Connection**.

![Data Analysis on AWS](/images/10/27.png?featherlight=false&width=90pc)

6. Select the Glue role created in the **Data Catalog** section as **AnalyticsworkshopGlueRole**.
  + Click **Test Connection**.

![Data Analysis on AWS](/images/10/28.png?featherlight=false&width=90pc)

This will take some time. Successful connection will display the message: **analytics_workshop connected successfully to your instance**.
Next we will proceed to create schema and tables on Redshift.
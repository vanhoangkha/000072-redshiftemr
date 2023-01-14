+++
title = "Create Redshift cluster"
date = 2021
weight = 2
chapter = false
pre = "<b>10.2 </b>"
+++


#### Create Redshift cluster

In this step, we will create 2 nodes Redshift cluster to create a small star schema database.

1. Go to [Redshift service administration interface](https://console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1)
  + Click **Create Cluster**.


![Data Analysis on AWS](/images/10/7.png?featherlight=false&width=90pc)

2. Set **Cluster identifier** to **redshift-cluster-1**.
  + Select **Node Type** as **dc2.large**.
  + Select **Number of Nodes** as ```2```.
  + Confirm **Configuration summary**.

![Data Analysis on AWS](/images/10/8.png?featherlight=false&width=90pc)

3. Let **Database port(optional)** be **5439**.
  + Change **Master user name** to ```admin```.
  + Enter **Master user password** .
  + Check the password setting rules before choosing a password (**This password will be used to access the cluster**).

![Data Analysis on AWS](/images/10/9.png?featherlight=false&width=90pc)

4. Expand the **Clusster permissions (optional)** section.
    + Select the pre-created role **Analyticsworkshop_RedshiftRole**.
    + Click **Add IAM Role**.
    + **Analyticsworkshop_RedshiftRole** will show up under **Attached IAM roles**.

![Data Analysis on AWS](/images/10/10.png?featherlight=false&width=90pc)

5. Leave **Additional configurations** as default. It will use default VPC and default security group
  + Click **Create Cluster**. It will take a few minutes for the cluster to change to ```available``` state.

![Data Analysis on AWS](/images/10/11.png?featherlight=false&width=90pc)

Once the cluster is created and the status is Available, go to the next step.

![Data Analysis on AWS](/images/10/12.png?featherlight=false&width=90pc)
+++
title = "Create schema and tables"
date = 2021
weight = 6
chapter = false
pre = "<b>10.6 </b>"
+++

#### Create schema and Redshift tables

1. Go to [Redshift service's Query Editor interface](https://us-east-1.console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1#query-editor) .
  + At the **Connect to database** page.
  + Select the Redshift cluster we created.
  + Select Database name as **dev**, and Database user as **admin**.
  + Click **Connect**.


![Data Analysis on AWS](/images/10/32.png?featherlight=false&width=90pc)


2. Run the following queries to generate the schema.

```
-- Create redshift_lab schema.
CREATE schema redshift_lab;
```


![Data Analysis on AWS](/images/10/33.png?featherlight=false&width=90pc)


1. Run the following queries to create a table for raw and reference data.
```
-- Create f_raw_1 table.
CREATE TABLE IF not EXISTS redshift_lab.f_raw_1 (
  uuid varchar(256),
  device_ts timestamp,
  device_id int,
  device_temp int,
  track_id int,
  activity_type varchar(128),
  load_time int
);
```

![Data Analysis on AWS](/images/10/34.png?featherlight=false&width=90pc)

```
-- Create d_ref_data_1 table.
CREATE TABLE IF NOT EXISTS redshift_lab.d_ref_data_1 (
  track_id int,
  track_name varchar(128),
  artist_name varchar(128)
);
```
![Data Analysis on AWS](/images/10/35.png?featherlight=false&width=90pc)

Next, we will perform the transformation and load the data into Redshift.
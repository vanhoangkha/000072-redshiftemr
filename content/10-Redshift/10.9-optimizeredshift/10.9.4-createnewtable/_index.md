+++
title = "Create new table"
date = 2021
weight = 4
chapter = false
pre = "<b>10.9.4 </b>"
+++

#### Create a new table and transfer data to the new table.

1. Based on all the optimization steps we have evaluated, we will proceed to create a new table.
  + Create a new column using the DDL of **f_raw_2** and **d_ref_data_2**

```
--fact table ddl
CREATE TABLE IF NOT EXISTS redshift_lab.f_raw_2 (
  uuid varchar(40) ENCODE zstd,
  device_ts timestamp,
  device_id int ENCODE az64,
  device_temp int ENCODE az64,
  track_id int ENCODE az64,
  activity_type varchar(16) ENCODE bytedict sortkey,
  load_time int ENCODE zstd
)
DISTKEY(track_id);
  
--dimension table ddl
CREATE TABLE IF NOT EXISTS redshift_lab.d_ref_data_2 (
  track_id int,
  track_name varchar(64),
  artist_name varchar(64)
)
DISTSTYLE ALL;
```

![Data Analysis on AWS](/images/10/59.png?featherlight=false&width=90pc)

2. Execute the following query to copy data from the old table to the new table.

```
--copy data from f_raw_1 to f_raw_2
insert into redshift_lab.f_raw_2 select * from redshift_lab.f_raw_1;
  
--copy data from d_ref_data_1 to d_ref_data_2
INSERT into redshift_lab.d_ref_data_2 select * from redshift_lab.d_ref_data_1;
```

![Data Analysis on AWS](/images/10/60.png?featherlight=false&width=90pc)

Next we will perform additional cleaning and data analysis steps after moving to the new table.
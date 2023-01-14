+++
title = "Data Check"
date = 2021
weight = 8
chapter = false
pre = "<b>10.8 </b>"
+++

#### Confirm - Data transformation went into Redshift

1. After the ETL script has run successfully, go to [Redshift service's Query Editor interface](https://ap-southeast-1.console.aws.amazon.com/redshiftv2/home?region=ap -southeast-1#query-editor).

  + Run the query below to check the number of records in the table of raw and reference data.

```
select count(1) from redshift_lab.f_raw_1;

select count(1) from redshift_lab.d_ref_data_1;
```

---

![Data Analysis on AWS](/images/10/55.png?featherlight=false&width=90pc)

2. Try running a more complex query on Redshift, note the execution time.

```
select
  track_name,
  artist_name,
  count(1) frequency
from
  redshift_lab.f_raw_1 fr
inner join
  redshift_lab.d_ref_data_1 drf
on
  fr.track_id = drf.track_id
where
  activity_type = 'Running'
group by
  track_name, artist_name
order by
  frequency desc
limit 10;
```
![Data Analysis on AWS](/images/10/56.png?featherlight=false&width=90pc)


You have completed loading data from S3 into Redshift using Glue Serverless ETL. Next we will perform some optimization steps to increase the performance of the query.
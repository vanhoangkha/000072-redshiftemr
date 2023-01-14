+++
title = "Query and performance comparison"
date = 2021
weight = 6
chapter = false
pre = "<b>10.9.6 </b>"
+++

#### Run Query and compare performance

1. Execute the query below, listing 10 songs with the same artist performing for a certain type of activity.

```--Top 10 tracks and corresponding artists for a particular activity type.
select
  track_name,
  artist_name,
  count(1) frequency
from
  redshift_lab.f_raw_2 fr
inner join
  redshift_lab.d_ref_data_2 drf
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

2. You can compare the execution time with the result of step **10.8** and compare the execution speed.
  + As on the image below, we can see that the execution time has been reduced from 12s to 2s for this query statement.

![Data Analysis on AWS](/images/10/63.png?featherlight=false&width=90pc)

Congratulations on completing the Data Analytics workshop on AWS. Hope this workshop will familiarize you with the services and features that make it easier to build data analytics solutions on AWS. .

{{% notice warning %}}
Make sure you do the cleanup after completing the lab, especially deleting the Glue dev endpoints and notebooks.
{{% /notice %}}
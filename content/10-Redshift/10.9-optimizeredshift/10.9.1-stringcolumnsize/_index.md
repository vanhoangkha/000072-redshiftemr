+++
title = "Optimize Column Size"
date = 2021
weight = 1
chapter = false
pre = "<b>10.9.1 </b>"
+++

#### Column size for string data.

1. Go to [Redshift service's Query Editor interface](https://ap-southeast-1.console.aws.amazon.com/redshiftv2/home?region=ap-southeast-1#query-editor).

  + We will perform a maximum length check of the columns based on the string.
  + All string-based columns should not be given a larger size than necessary. It reduces the storage space on the Redshift cluster and also improves query performance when you use these columns in the query by consuming less memory.

```
select max(len(uuid)) as uuid_len, max(len(activity_type)) as activity_type_len from redshift_lab.f_raw_1;
      
select max(len(track_name)) as uuid_len, max(len(artist_name)) as activity_type_len from redshift_lab.d_ref_data_1;
```

![Data Analysis on AWS](/images/10/57.png?featherlight=false&width=90pc)

2. The results from the above query will be used to determine the new precision for columns with string data.

![Data Analysis on AWS](/images/10/58.png?featherlight=false&width=90pc)

3. Learn more about limiting column size [here](https://docs.aws.amazon.com/redshift/latest/dg/c_best-practices-smallest-column-size.html).
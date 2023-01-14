+++
title = "Vacuum and Analyze"
date = 2021
weight = 5
chapter = false
pre = "<b>10.9.5 </b>"
+++

#### Perform Vacuum and Analyze

1. In this step we will run the vacuum and analyze on the new table we just created.

**VACUUM**: Reorder rows and reclaim space in a specified table or all tables in a specified database.

**ANALYZE**: Update table statistics for use by **query planner** system, to optimize the way Redshift queries data.

2. Run the following query in the Query Editor.

```
vacuum redshift_lab.f_raw_2;
analyze redshift_lab.f_raw_2;

```
![Data Analysis on AWS](/images/10/61.png?featherlight=false&width=90pc)

3. Continue

```
vacuum redshift_lab.d_ref_data_2;
analyze redshift_lab.d_ref_data_2;
```
![Data Analysis on AWS](/images/10/62.png?featherlight=false&width=90pc)

Next, we will perform a data query on the new table after all the operations we have optimized.
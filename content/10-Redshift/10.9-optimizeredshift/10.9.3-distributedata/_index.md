+++
title = "Data Delivery"
date = 2021
weight = 3
chapter = false
pre = "<b>10.9.3 </b>"
+++

#### Distribution Style and Sort Keys

Distribution / Data distribution is an important performance optimization method on Redshift. Good data distribution reduces the amount of data that has to be moved back and forth between the nodes in the Redshift cluster.

1. We will use a **KEY** based distribution for the **f_raw_1** data table.
  + Since the two tables (**f_raw_1** and **d_ref_data_1**) need to be merged on the **track_id** column, we will choose **track_id** as the distribution key.
  

2. We will use the **ALL** distribution for the dimension table - **d_ref_data_1**.

3. Learn more about Redshift Distribution style [here](https://docs.aws.amazon.com/redshift/latest/dg/c_choosing_dist_sort.html).

4. In our queries, the **activity_type** attribute has been used to filter for equality, so we will choose this attribute as the sort column.
  + Selecting a column that is often used to filter (filter) as a column to sort the data in the table will help the query become faster.

5. Learn more about Redshift's best practices when using sort keys [here](https://docs.aws.amazon.com/redshift/latest/dg/c_best-practices-sort-key.html)
+++
title = "Compression"
date = 2021
weight = 2
chapter = false
pre = "<b>10.9.2 </b>"
+++

#### Compression

In this step, we will analyze the raw table to choose the appropriate compression algorithm.

1. Check the appropriate algorithm on each table to perform compression.
  Compression is a column-level operation to reduce the size of data as it is stored. Compression helps optimize storage space and reduce the size of data read from storage, while reducing the amount of I/O to disk and improving query performance.
  + Run the following query in the Query Editor interface.

```
analyze compression redshift_lab.f_raw_1;
```

![Data Analysis on AWS](/images/10/58.png?featherlight=false&width=90pc)

2. The results from the table above provide the following information for each column:

  + Column Name
    Encoding: Recommended compression based on column type and precision value.
    + Est_reduction_pct: The estimated percentage reduction if the proposed compression method is implemented.
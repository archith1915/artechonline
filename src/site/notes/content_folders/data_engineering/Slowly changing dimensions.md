---
{"dg-publish":true,"permalink":"/content-folders/data-engineering/slowly-changing-dimensions/","title":"Slowly Changing Dimensions","tags":["dataEngineering","data"],"dgShowToc":true}
---

# SCD 1

In SCD 1, whenever there is a change, the value is overwritten and no history is maintained. 

![scd1.png](/img/user/assets/data_engineering/scd/scd1.png)


# SCD 2

In SCD 2, history of changes is maintained and a new entry is created for each change. This can be achieved through multiple ways. 

## Using flags

A new column can be added to store the flag indicating the status of the versions. The one with a true flag is the current and latest version while.

![scd2_flag.png](/img/user/assets/data_engineering/scd/scd2_flag.png)

## Using version numbers

Version numbers can be used to indicate changes made in the data. The version with the highest value happens to be the latest one.

![scd2_version.png](/img/user/assets/data_engineering/scd/scd2_version.png)

## Using date range

Date ranges (start and end dates) can be used to indicate when a value was over written thus leaving the latest version with no end date (NULL value).

![scd2_dateRange.png](/img/user/assets/data_engineering/scd/scd2_dateRange.png)

# SCD 3

SCD 3 stores partial history of the data and the changes made to it. It only stores the value of the immediate previous version with the current value in a separate column.

![scd3.png](/img/user/assets/data_engineering/scd/scd3.png)

# SCD 6

SCD 6 is a combination of [[content_folders/data_engineering/Slowly changing dimensions#SCD 1\|SCD 1]], [[content_folders/data_engineering/Slowly changing dimensions#SCD 2\|SCD 2]], and [[content_folders/data_engineering/Slowly changing dimensions#SCD 3\|SCD 3]]. 

![scd6.png](/img/user/assets/data_engineering/scd/scd6.png)
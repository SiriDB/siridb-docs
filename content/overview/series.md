---
title: "Series"
weight: 9
---

**Series** or **time series** can be seen as lists of data points. Time series in SiriDB are uniquely identified by name and can have any number of points. A single point consists of a timestamp and value. SiriDB allows you to insert points in any order. That way it is possible to backfill the database with old data while new values are coming in as well.

![Time series](../../images/time-series.png)

SiriDB supports time series for numeric data types (integer or float) and strings. You do not need to specify the type in advance. When inserting data into SiriDB, new time series will be created automatically for the correct data type. Time series can be queried by name, regular expressions or dynamic groups.
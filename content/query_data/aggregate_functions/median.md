---
title: "median"
weight: 39
---

The median is a robust measure of central location, and is less affected by the presence of outliers in your data. When the number of data points is odd, the middle data point is returned as float value. When the number of data points is even, the median is interpolated by taking the average of the two middle values.

If no time window is provided it returns the median of the series.

### Function

    median([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

A float value.

### Example

    # Select the median grouped by 1 minute and return the difference for that result
    select median(1m) => difference() from "series-001"

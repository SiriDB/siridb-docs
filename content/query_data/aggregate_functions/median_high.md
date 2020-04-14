---
title: "median high"
weight: 38
---


The high median is always a member of the data set. When the number of data points is odd, the middle value is returned. When it is even, the larger of the two middle values is returned.

If no time window is provided it returns the median_high of the series.

### Function

    median_high([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

An integer or float value depending on the series data type.

### Example

    # Select the median_high grouped by 1 minute and return the difference for that result
    select median_high(1m) => difference() from "series-001"

---
title: "median low"
weight: 31
---

The low median is always a member of the data set. When the number of data points is odd, the middle value is returned. When it is even, the smaller of the two middle values is returned.

If no time window is provided it returns the median_low of the series.

### Function

Syntax:

    median_low([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

An integer or float value depending on the series data type.

### Example

    # Select the median_low grouped by 1 minute and return the difference for that result
    select median_low(1m) => difference() from "series-001"

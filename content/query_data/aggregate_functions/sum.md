---
title: "sum"
weight: 47
---

Sum can be used when you want to know the sum of the values over a period of time. If no time window is provided it returns the sum of the values in the series.

### Function

    sum([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

An integer or float value depending on the series data type.

### Example

    # Get the sum of the values collected over the last 24 hours per hour.
    select sum(1h) from "series-001" between now - 1d and now

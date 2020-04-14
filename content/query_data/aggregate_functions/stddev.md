---
title: "stddev"
weight: 42
---

Returns the standard deviation which is the square root of its variance. If no time window is provided it returns the standard deviation of the series.

### Function

    stddev([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

A float value.

### Example

    # Select standard deviation grouped by 1 hour.
    select stddev(1h) from 'series-001'

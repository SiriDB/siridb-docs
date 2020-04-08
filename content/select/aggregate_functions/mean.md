---
title: "mean"
weight: 28
---

Mean is used to calculate the average values per selected time window.

If no time window is provided it returns the mean of the series.

### Function

Syntax:

    mean([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

A float value.

### Example

    # Get average value of 'series-001' up until now.
    select mean(now) from "series-001" before now

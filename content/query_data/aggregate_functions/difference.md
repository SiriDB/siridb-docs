---
title: "difference"
weight: 32
---

The difference between the first value and the last value within the time window.

Difference without a time span argument will return the difference between values.

### Function

    difference([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
 ts (optional) | Time window; the difference between the first value and the last value within the time window.

### Return value

An integer or float value depending on the series data type.

### Example

    # Select difference between values in series-001.
    select difference() from 'series-001'

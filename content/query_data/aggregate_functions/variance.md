---
title: "variance"
weight: 49
---

Returns the sample variance of data, an iterable of at least two real-valued numbers. Variance is a measure of the variability (spread or dispersion) of data. A large variance indicates that the data is spread out; a small variance indicates it is clustered closely around the mean.

If no time window is provided it returns the variance of the series.

### Function

     variance([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

A float value.

### Example

    # Select the variance grouped by 1 minute
    select variance(1m) from "series-001"

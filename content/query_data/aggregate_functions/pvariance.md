---
title: "pvariance"
weight: 44
---

Returns the population variance of data, a non-empty iterable of real-valued numbers. Variance is a measure of the variability (spread or dispersion) of data. A large variance indicates that the data is spread out; a small variance indicates it is clustered closely around the mean.

If no time window is provided it returns the pvariance of the series.

### Function

    pvariance([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

A float value.

### Example

    # Select the pvariance grouped by 1 minute
    select pvariance(1m) from "series-001"

---
title: "first"
weight: 34
---

Returns the first value in each `ts` time window. Or if no time window is provided it just returns the first value of the series.

### Function

    first([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

An integer, float or string value depending on the series data type.

### Example

    # Select the first value from 'series-001'
    select first() from 'series-001'

    # Select the first value per day from 'series-001'
    select first(1d) from 'series-001'

    # Select the first value in 2018 from 'series-001'
    select first() from 'series-001' after '2018'

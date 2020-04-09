---
title: "last"
weight: 30
---


Returns the last value in each `ts` time window. Or if no time window is provided it just returns the last value of the series.

### Function

Syntax:

    last([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

The last value in each `ts` time window or just the last value if no time window is provided.

### Example

    # Select the last value from 'series-001'
    select last() from 'series-001'

    # Select the last value per day from 'series-001'
    select last(1d) from 'series-001'

    # Select the last value in 2017 from 'series-001'
    select last() from 'series-001' before '2018'

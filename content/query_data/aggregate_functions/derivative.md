---
title: "derivative"
weight: 29
---

The derivative can be used to get the difference per time unit. When no optional arguments
are used the difference per one unit is returned. For example, in a database with second
precision the return value will be the difference per second.

### Function

   derivative([ts [, ts]])

### Arguments

 Arguments   | Description
 ----------- | -----------
 ts (optional) | Time unit; difference per given time unit
 second ts (optional) | Time window; used to get the difference between the first and last value within the given time window.

### Return value

A float value.

### Example

    # Select the difference per second for values in series-001.
    select derivative(1s) from 'series-001'

    # Select the difference per second between the first and last value
    # within each hour for values in 'series-001'
    select derivative(1s, 1h) from 'series-001'

---
title: "derivative"
weight: 18
---

Syntax:

   derivative([ts [, ts]])

Returns a float value.

The derivative can be used to get the difference per time unit. When no optional arguments
are used we return the difference per one unit. For example, in a database with second
precision the return value will be the difference per second. Optionally another time unit can
be used. A second argument can be used to set a time period. This time period will be used to get the difference between the first and last value within the time window.

Example:

    # Select the difference per second for values in series-001.
    select derivative(1s) from 'series-001'

    # Select the difference per second between the first and last value
    # within each hour for values in 'series-001'
    select derivative(1s, 1h) from 'series-001'

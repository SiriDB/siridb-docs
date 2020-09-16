---
title: "interval"
weight: 34
---


Returns the difference between the timestamps. This function will give the same result as `timeval() => difference()` but is slightly faster.
Since all timestamps are in order, the difference will always be a positive value.

### Function

    interval()

### Arguments

None

### Return value

The returned series will contain the difference between timestamps as their values. The timestamp of the difference is the *latest* of the two compared timestamps.

### Example

    # Select the interval between timestamps from 'series-001'
    select interval() from 'series-001'

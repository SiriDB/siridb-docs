---
title: "timeval"
weight: 46
---


Returns the timestamp of series as their values. By itself this is not very useful but it might be combined with another aggregation function to get a specific result.
SiriDB has function [interval()](../interval) for the common combination `timeval() => difference()`.

### Function

    timeval()

### Arguments

None

### Return value

The returned series will contain points where each point will have a value equal to the timestamp.

### Example

    # Select the timestamps as values from 'series-001'
    select timeval() from 'series-001'

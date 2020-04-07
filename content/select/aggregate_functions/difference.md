---
title: "difference"
weight: 19
---

Syntax:

    difference([ts])

Returns an integer or float value depending on the series data type.

Difference without arguments is used to get the difference between values.
As an optional argument you can specify a time period. In this case the function returns the difference between the first value and the last value within the time window.

Example:

    # Select difference between values in series-001.
    select difference() from 'series-001'

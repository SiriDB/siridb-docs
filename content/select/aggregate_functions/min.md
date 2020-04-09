---
title: "min"
weight: 37
---

Min is the opposite of max, you identify the lowest value in the selected time window. If no time window is provided it returns the lowest value of the series.

### Function

Syntax:

    min([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

An integer or float value depending on the series data type.

### Example

    # Get the minimum value per day from 'series-001' between two dates.
    select min(1d) from "series-001" between '2016-11-14' and '2016-11-21'

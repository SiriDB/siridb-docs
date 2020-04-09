---
title: "max"
weight: 32
---

Max can be used to identify the highest value in the selected time window. If no time window is provided it returns the highest value of the series.

### Function

Syntax:

    max([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
ts (optional) | Time window.

### Return value

An integer or float value depending on the series data type.

### Example

    # Get the maximum value in 'series-001' over the last week.
    select max(now) from "series-001" between now - 1w and now

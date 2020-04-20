---
title: "count"
weight: 29
---

Returns the number of points over a time window.

If no time window is provided it returns the total number of points in the series.

### Function

    count([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
 ts (optional) | Time window. It can also be a timestamp that determines the end of the first time bucket starting at 1970-01-01.

### Return value

An integer value.

### Example

Count can be used to calculate points over a period of time.

Example:

    # Get the number of points in 'series-001' over the past 24 hours.
    select count(now) from "series-001" between now - 1d and now

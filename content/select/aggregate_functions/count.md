---
title: "count"
weight: 17
---

Returns the number of points.

### Function

Syntax:

    count([ts])

### Arguments

 Arguments   | Description
 ----------- | -----------
 ts (optional) | A timestamp. It determines the end of the time span over which the number of point are counted. If there are points beyond the end point, they will be captured in a second time span that ends at `ts+(ts-1970)`.

### Return value

An integer value.

### Example

Count can be used to calculate points over a period of time.

Example:

    # Get the number of points in 'series-001' over the past 24 hours.
    select count(now) from "series-001" between now - 1d and now

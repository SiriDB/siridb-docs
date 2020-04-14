---
title: "limit"
weight: 34
---

Returns no more than the provided number of points and in case more points are found the aggregation function is used to reduce the number of points.

### Function

    limit(max_points, aggr_function)

### Arguments

 Arguments   | Description
 ----------- | -----------
max_points | Maximum number of points that gets returned.
aggr_function | Aggregation function used if needed.

### Return value

Returns at most `max_points` and uses a given aggregation function to reduce
the number of points if needed.

### Example

    # Returns at most 100 points for 'my-series'. The original values are
    # returned in case hundred or less points are found. In case more points
    # are found a mean aggregation function is used.
    select limit(100, mean) from "my-series"

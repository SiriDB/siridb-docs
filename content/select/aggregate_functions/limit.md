---
title: "limit"
weight: 23
---

Syntax:

    limit(max_points, aggr_function)

Returns at most `max_points` and uses a given aggregation function to reduce
the number of points if needed.

Example:

    # Returns at most 100 points for 'my-series'. The original values are
    # returned in case hundred or less points are found. In case more points
    # are found a mean aggregation function is used.
    select limit(100, mean) from "my-series"

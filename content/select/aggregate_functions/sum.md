---
title: "sum"
weight: 32
---

Syntax:

    sum([ts])

Returns an integer or float value depending on the series data type.

Sum can be used when you want to know the sum of the values over a period of time.

Example:

    # Get the sum of the values collected over the last 24 hours per hour.
    select sum(1h) from "series-001" between now - 1d and now

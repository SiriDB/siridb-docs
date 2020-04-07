---
title: "min"
weight: 29
---

Syntax:

    min([ts])

Returns an integer or float value depending on the series data type.

Min is the opposite of max, you identify the lowest value in the selected time window.

Example:

    # Get the minimum value per day from 'series-001' between two dates.
    select min(1d) from "series-001" between '2016-11-14' and '2016-11-21'

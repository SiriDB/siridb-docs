---
title: "max"
weight: 24
---

Syntax:

    max([ts])

Returns an integer or float value depending on the series data type.

Max can be used to identify the highest value in the selected time window.

Example:

    # Get the maximum value in 'series-001' over the last week.
    select max(now) from "series-001" between now - 1w and now

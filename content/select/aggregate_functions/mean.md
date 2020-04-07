---
title: "mean"
weight: 25
---

Syntax:

    mean([ts])

Returns a float value.

Mean is used to calculate the average values per selected time window.

Example:

    # Get average value of 'series-001' up until now.
    select mean(now) from "series-001" before now

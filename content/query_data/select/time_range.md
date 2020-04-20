---
title: "time range"
weight: 26
---

An optional time range can be given to select only a part of the series data.
If no time range is provided SiriDB returns all the data available. As a time
range we can use *before*, *after* or *between .. and ..*

When using `after` you basically set a *start* time, with `before` an *end* time
and when using `between .. and ..` you set both a *start* and *end* time.
Points that have the exact start time are *included* in the result, points
with the exact end time are *excluded* from the result.

>**Note**
>
>It's safe to use *now* multiple times in a query. SiriDB only calculates *now* one
>time while processing a query. This way you can be sure that *now* has the
>same value.

### Examples

    # Select all points from "series-001" in the last 24h
    select * from "series-001" after now - 1d

    # Select all points from "series-001" today
    select * from "series-001" between now - (now % 1d) and now - (now % 1d) + 1d

    # Select all points from "series-001" before November, 2015
    select * from "series-001" before "2015-11"

---
title: "range"
weight: 27
---

An optional time, or head/tail range can be given to select only a part of the series data.
If no range is provided SiriDB returns all the data available. As a range we can use *before*, *after*, *between .. and ..*, *head* or *tail*.

When using `after` you basically set a *start* time, with `before` an *end* time
and when using `between .. and ..` you set both a *start* and *end* time.
Points that have the exact start time are *included* in the result, points
with the exact end time are *excluded* from the result.

### Allowed formats

The allowed formats for time ranges are:

- **Integer values**: Number of time units after 1970-01-01. The time unit depends on the database time precision. For example, seconds.
- **Time values**: `w` (week), `d` (day), `h` (hour), `m` (minute) and `s` (second). For example, `2w` is equal to two weeks.
- **Date/time strings**: For example `"2021"`, `"2021-01-30"`, `"2021-01-30 12:00"`, `"2021-01-30 14:31:45Z"`, `"2021-01-30T14:31:45+0200"`.
- **now**: A keyword referring to the current date/time.

>**Note**
>
>It's safe to use *now* multiple times in a query. SiriDB only calculates *now* one
>time while processing a query. This way you can be sure that *now* has the
>same value.

It is also possible to ask for the first or last *X* points from series by using `head` and `tail` respectively followed by an integer value.

### Examples

    # Select all points from "series-001" in the last 24h
    select * from "series-001" after now - 1d

    # Select all points from "series-001" today
    select * from "series-001" between now - (now % 1d) and now - (now % 1d) + 1d

    # Select all points from "series-001" before November, 2015
    select * from "series-001" before "2015-11"

    # Select the last 10 points from "series-001"
    select * from "series-001" tail 10

    # Select the first 5 points from "series-001"
    select * from "series-001" head 5

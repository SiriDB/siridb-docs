---
title: "aggregate functions"
weight: 19
---


SiriDB supports multiple build-in aggregation and filter functions. Using these functions can be useful to reduce network traffic.

List of the supported aggregation and filter functions:

- [count](./count)
- [derivative](./derivative)
- [difference](./difference)
- [filter](./filter)
- [first](./first)
- [last](./last)
- [limit](./limit)
- [max](./max)
- [mean](./mean)
- [median_high](./median_high)
- [median_low](./median_low)
- [median](./median)
- [min](./min)
- [pvariance](./pvariance)
- [stddev](./stddev)
- [sum](./sum)
- [variance](./variance)

### Multiple aggregate functions in one query

It's possible to select multiple aggregate functions in one query. This has some
advantages over performing multiple queries since the database in this case only
needs to search for the series and points once. To find the requested aggregate
in the result we must add a prefix and/or suffix to the series name to make the
name unique.

>**Note**
>
>A prefix and/or suffix is only required when querying multiple aggregates.

Example:

    # Select both the min and max grouped by 5 minutes from "series-001"
    select min(5m) prefix "min-", max (5m) prefix "max-" from "series-001"

The aggregate functions can be used together by parsing the result of one function
to the next. It's also possible to use the same function twice which can be
useful with for example difference.

Example:

    # Select the median grouped by 1 minute and return the difference for that result
    select median (1m) => difference () from "series-001"

### Time span argument

Most aggregation functions accept an optional `ts` (time span) argument. When you take a time span of 1w for example. Then there will be 'buckets' created with a length of 1 week. Be aware that the start is always at 1970-01-01. So if you have a time series between 2020-04-06 and 2020-04-21, a `ts` of 1w will result in 3 buckets that end at 2020-04-09, followed by 2020-04-16 and 2020-04-23. So the first bucket does not end a week from April 6th, as you may expect.

`ts` can also be a timestamp where you can use `now` for example. This determines the end of the first bucket. The beginning starts at 1970-01-01. If there are points beyond that timestamp, they will be captured in subsequent buckets.

When the time span is not provided, SiriDB will usually return the last timestamp in the result. One exception is the `first()` function which will return the first timestamp instead.

For example:

    # Select the last time-stamp and the average over all values.
    select mean() from `my_series`

    # Select the first time-stamp and first value:
    select first() from `my_series`

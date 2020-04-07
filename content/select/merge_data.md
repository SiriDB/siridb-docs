---
title: "merge data"
weight: 34
---

When selecting points from multiple series you can merge the data together in
result. Most of the time you also want to provide an aggregate function with the
merge so series get really merged into one series. Even with merge it's still
possible to use aggregate functions on the series before they are merged.

>**Note**
>
>Sometimes it does not matter for the end result if you use an aggregate
>function on the series or only while merging. However, if you have multiple
>pools it can be an advantage to aggregate the series and the merge. This is
>an advantage because each pool can do some aggregate work and only send the
>aggregated result to the server processing the query.
>
>For example:
>
>`select * from /series.*/ merge as "series" using sum(1h)`
>
>will have the exact same result as
>
>`select sum(1h) from /series.*/ merge as "series" using sum(1h)`
>
>but the last one will be faster, assuming you are using a SiriDB cluster and
>/series.*/ contains multiple series spread out over multiple pools.

Examples:

>**Note**
>
>In the examples below we assume there are no points in the future. If you have
>points in the future and only want points from 7 days ago up till now you can
>use between now - 7d and now. Since we assume our series have no points in the
>future we use after now - 7d.

    # We want the average value per 1 hour over the last 7 days over s01
    # and s02. The series should weight equal to each other but s01 has
    # a point each 2 seconds while s02 only has a point each 5 seconds.
    # We solve this by first getting the mean value for each series
    # by 1 hour before merging the series.
    #
    # Note that we use mean(1) while merging. This means we group by 1 second or
    # millisecond depending on the time precision. We can do this because the
    # series are already grouped by 1h and therefore have re-indexed timestamps
    # at precisely each hour.
    select mean(1h) from "s01", "s02" after now - 7d merge as "merged_s" using mean(1)

    # We want the number of points s01 and s02 have over the last 7 days.
    # Note: when having no timestamps after now this will result in one
    #       value with timestamp *now*
    select count(now) from "s01", "s02" after now - 7d merge as "merged_s" using sum(1)

    # We have s01 and s02 representing counter data. We want to sum the
    # values per 4 hours over January, 2015 and show this as one series.
    select sum(4h) from "s01", "s01" between "2015-01" and "2015-02" merge as "merged_s" using sum(1)

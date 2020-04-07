---
title: "last"
weight: 22
---

Syntax:

    last([ts])

Returns the last value in each `ts` time window. (Or just the last value)

Example:

    # Select the last value from 'series-001'
    select last() from 'series-001'

    # Select the last value per day from 'series-001'
    select last(1d) from 'series-001'

    # Select the last value in 2017 from 'series-001'
    select last() from 'series-001' before '2018'

---
title: "first"
weight: 21
---

Syntax:

    first([ts])

Returns the first value in each `ts` time window. (Or just the first value)

Example:

    # Select the first value from 'series-001'
    select first() from 'series-001'

    # Select the first value per day from 'series-001'
    select first(1d) from 'series-001'

    # Select the first value in 2018 from 'series-001'
    select first() from 'series-001' after '2018'

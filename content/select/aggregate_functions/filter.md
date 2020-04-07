---
title: "filter"
weight: 20
---

Syntax:

    filter(<operator> <value>)

Returns an integer, float or string value depending on the series data type.

Filter is used to filter the result by values.

Example:

    # Select all values from 'series-001' except where the value is 0
    select filter(!= 0) from 'series-001'

    # Select all positive values from 'series-001'
    select filter(> 0) from 'series-001'

    # Select all values containing 'error' and not 'unavailable
    select filter(~'error') => filter(!~'unavailable') from 'some-log-series'

    # Select all values starting with 'error' using a regular expression
    select filter(/error.*/) from 'some-log-series'

    # Filter out Not-a-number (nan) and Infinite values
    select filter(!=nan) => filter(!=inf) => filter(!=-inf) from 'some-float-series'

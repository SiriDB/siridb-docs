---
title: "filter"
weight: 31
---

Filter is used to filter the result by testing it to a value, regular expression or condition.

### Function

    filter(val_regex_or_condition)

### Arguments

 Arguments   | Description
 ----------- | -----------
val_regex_or_condition | A value, regular expression or condition

### Return value

An integer, float or string value depending on the series data type.

### Example

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

---
title: "columns"
weight: 94
---

Valid columns are:

- pool: Returns the pool ID.
- series: Number of series in the pool.
- servers: Number of servers in the pool.

When no columns are provided the default is used. (pool, servers, series)

### Examples

    # list pools with more than 1000 series
    list pools where series>1000

    #list all series by pool and series
    list pools pool, series

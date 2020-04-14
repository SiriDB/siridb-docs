---
title: "drop series"
weight: 51
---

Drops series from SiriDB. Optionally you can use a match and/or where statement
to filter the series you want to drop. For more information about how to match
series look at [list series](../list_series).

SiriDB has a mechanism to protect you from accidentally dropping all (or many)
series. This is done with a *threshold* value. If the server receives a drop
request that contains more series than the threshold, the request
is denied and you receive an *error_msg*. The *drop_threshold* value will not be checked by other
servers in the cluster.

You can view the current *drop_threshold* with `show drop_threshold`. See [alter database](../../database/alter_database) on how to change this value. The default drop threshold is set to 1 (100%) which means you cannot drop *all* series but any other amount will pass. The drop threshold can be set to a value between 0 and 1. For example a value of 0.5 means you cannot drop more than 50% of the available series.

It is also possible to ignore the *drop_threshold* for one request by adding *set ignore_threshold true*.

>**Tip**
>
>Before using a regular expression to drop series, you can check the
>expression first using `count series` and/or `list series` and see if your
>match has the expected result.

### Syntax

    drop series [series_match] [where ...] [set ignore_threshold true/false]

### Examples

    # Drop series "series-001"
    drop series "series-001"

    # Drop all series
    drop series set ignore_threshold true

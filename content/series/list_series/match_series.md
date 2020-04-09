---
title: "match series"
weight: 48
---

Series can be matched using different methods. [Groups](../../../groups) can help to quickly get the required series even in a database with millions of unique series.

Syntax:

    <series_name | regular_expression | group> [update_function <match_series>]

#### Series name

A series name is a string containing the series name.

An advantage of using series names in a SiriDB cluster is that we know in which pool the series exists, because SiriDB sends data to a pool based on the series name. The given query will therefore only be send to the applicable pool(s). When using a regular expression or group match we don't know which pool contains the series, so each pool needs to be queried.

Example:

    list series 'series-001'

#### Regular expression

Regular expressions can be used to select series.

>**Note**
>
>Each pool in a SiriDB cluster will look for matching series. If you plan to use a regular expression multiple times, you should consider creating a group for the expression.

Example:

    # list all series starting with "linux"
    list series /linux.*/

    # list all series starting with "linux" (case-insensitive)
    list series /linux.*/i

    # list all series not starting with "linux"
    list series /(?!linux).*/

    # list all series not containing "linux"
    list series /((?!linux).)*/

#### Group

[Groups](../../../groups) are basically cached regular expression and can be used together with normal
regular expressions. When you use a regular expression to match series in a group it's
best to first select the group and then the regular expression. This way the regular
expression only needs to validate series inside the group.

Examples:

    # list all series in group "linux"
    list series `linux`

    # list all series in group "linux" with "cpu" in the name
    # note that we first select the group so the regular expression only
    # needs to be validated on series in the group.
    list series `linux` & /.*cpu.*/

#### Update functions

When selecting series you can combine *series-names*, *regular-expressions* and *groups*. Update functions tell SiriDB how to combine the selection.
SiriDB knows four update functions:

* difference (alias: **-**)
* symmentric_difference (alias: **^**)
* union (aliases: **,** and **|**)
* intersection (alias: **&**)

Examples:

    # list multiple series using union (we actually use the alias here)
    list series 'series-001', 'series-002', 'series-003'

    # list series in group "linux" except series which are also in group "cpu"
    list series `linux` - `cpu`

    # list series when member of group "linux" or group "cpu" but not both
    list series `linux` ^ `cpu`

    # list series that are both members of `linux` and `cpu` except when
    # a series name contains "test".
    list series `linux` & `cpu` - /.*test.*/

    # list series in group `linux` and view their length.
    list series name, length `linux`

    # list series in group `linux` which have their last data point more
    # than 100 days ago
    list series `linux` where end < now - 100d


    # sample output (list series)
    {
        "columns": ["name"],
        "series": [
            ["series-001"],
            ["series-002"]
        ]
    }

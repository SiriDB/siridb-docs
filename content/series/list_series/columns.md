---
title: "columns"
weight: 53
---

Valid columns are:

- name: Series name
- pool: Pool where the series is assigned to
- start: Time-stamp of the first value in the series
- end: Time-stamp of the last value in the series
- length: The number of points in a series
- type: The series type. ("integer", "float" or "string")
- shard_duration: The shard duration for this series on this particular SiriDB server (`0` for series which only use the buffer)

When no columns are provided the default is used. (name)

### Examples

    # list all series starting with "linux" by name
    list series /linux.*/

    # list all series starting with "linux" by name, type, length and pool
    list series name, type, length, pool /^series.*/

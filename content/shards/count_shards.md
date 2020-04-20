---
title: "count shards"
weight: 56
---

Count shards returns the number of shards on all *online* servers in a SiriDB
cluster. This means that offline servers are ignored and replica servers are
included in the query.
It's also possible to count the shards size in case you want to see the amount
of disk-space the shards are using.

### Syntax

    count shards [size] [where ...]

### Examples

    # Get number of shards
    count shards

    # Get number of shards for the current points. (assuming you have
    # no shards for points in the future)
    count shards where end > now

    # Get the amount of disk space (in bytes) which shards are using
    # on server01.
    count shards size where server == 'server01'

Example output (count shards):

    {"shards": 51}

Example output (count shards size):

    {"shards_size": 355243846}

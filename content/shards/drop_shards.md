---
title: "drop shards"
weight: 64
---

Drops an existing shard using the shard id (sid). Use `list shards` for an
overview of the current shards. This statement requires all pools to have at
least one online server. The number of dropped shard in the result message
only contains the dropped shards of one member of a pool, not the shards which
are dropped by a replica. This is different from the `count shards` statement
which includes the shards on replica servers as well.

>**Note**
>
>This statement is protected with a *threshold*. See [drop series](../../series/drop_series) and [alter database](../../database/alter_database) for more information about this threshold value.

### Syntax

    drop shards [where ...] [set ignore_threshold true/false]

### Example

    # Drop shards for points which are older than one year
    drop shards where end < now - 52w

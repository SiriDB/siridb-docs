---
title: "expiration log"
weight: 84
---

This settings should be an integer value with the time precision of the database.

For example:

```siridb
# Suppose we have a second precision database,
# then this will drop log shards, older than 4 weeks
alter database set expiration_log 3600*24*7*4

# Disable shard expiration:
    alter database set expiration_log 0
```

When setting the expiration so that more than the drop_threshold of the current shards will be dropped, an error is displayed and set ignore_threshold true may be added to ignore this warning.

Example:
```siridb
set expiration_log 52w set ignore_threshold true
```

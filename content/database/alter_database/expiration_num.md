---
title: "expiration num"
weight: 105
---

When the *expiration_num* is enabled than number shards that are older than the provided value will be dropped. This setting should be an integer value with the time precision of the database.

By default this setting is disabled.

### Examples

```siridb
# Suppose we have a second precision database,
# then this will drop number shards, older than 4 weeks
alter database set expiration_num 3600*24*7*4

# Disable shard expiration:
alter database set expiration_num 0
```

After setting the expiration_num that results in more shards being dropped than the drop_threshold allows, an error is displayed and *set ignore_threshold true* may be added to ignore this warning.

```siridb
alter database set expiration_num 52w set ignore_threshold true
```

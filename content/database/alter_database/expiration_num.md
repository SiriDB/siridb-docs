---
title: "expiration num"
weight: 77
---

This settings should be an integer value with the time precision of the database.

For example:

```siridb
# Suppose we have a second precision database,
# then this will drop number shards, older than 4 weeks
alter database set expiration_num 3600*24*7*4
```

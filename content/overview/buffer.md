---
title: "Buffer"
weight: 11
---

A server receives data and stores this in a buffer. The buffer is immediately saved on disk and is also kept in memory. The buffer can store a fixed number of points for each time series. This number depends on the buffer size which can be configured when creating a database. Since SiriDB does not read from the buffer-file, it does not matter in which order the points are saved. In memory the points are saved in order so queries can return the points from the buffer very fast.

![Buffer file](../../images/buffer-file-memory.png)

When the buffer for a time series is “full” and new points can't be saved, then both the new, and the buffer data will be sent to shards.

![Buffer to shards](../../images/buffer-to-shards.png)

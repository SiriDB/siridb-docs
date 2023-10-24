---
title: "offset"
weight: 44
---

Set a different offset for the time window in the previous aggregation. This aggregation mush therefore be used after an aggregation function like mean, min, max etc.

### Function

    offset(ts)

### Arguments

 Arguments   | Description
 ----------- | -----------
 ts          | Offset.

### Return value

A float value.

### Example

    # Select the mean grouped by 1 day using a two hours offset
    select mean(1d) => offset(2h) from "series-001"

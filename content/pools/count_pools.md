---
title: "count pools"
weight: 78
---

Count pools in the SiriDB cluster.

### Syntax

    count pools [where ...]

### Examples

    # Get number of pools
    count pools

    # Count the pools with more than 1000 series
    count pools where series > 1000

Example output:

    {"pools":2}

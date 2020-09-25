---
title: "list limit"
weight: 105
---

Change the maximum value which can be used as a limit for a list statement. The default and recommended value is set to ten thousand to prevent queries which could take a large amount of memory. The value must be greater than or equal to 1000.

### Example

    # Set the list limit to 50 thousand.
    alter database set list_limit 50000

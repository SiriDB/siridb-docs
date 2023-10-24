---
title: "alter servers"
weight: 89
---

You can alter the *log_level* for *n* servers at once. Changing the log level is explained in more detail at [alter server](../alter_server).

### Syntax

    alter servers [where...] set <option>

### Example

    # Change the log-level to "debug"
    alter servers where uuid == 'f851c6a4-820e-11e5-9661-080027f37001' set log_level debug

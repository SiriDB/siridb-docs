---
title: "alter servers"
weight: 73
---

You can alter the *tee_pipe_name* and/or *log_level* for *n* servers at once. Changing the tee pipe name and log level is explained in more detail at [alter server](../alter_server).

### Syntax

    alter servers [where...] set <option>

### Example

    # Change the log-level to "debug"
    alter servers where uuid == 'f851c6a4-820e-11e5-9661-080027f37001' set log_level debug

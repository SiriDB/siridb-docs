---
title: "alter servers"
weight: 72
---

You can alter the *tee_pipe_name* and/or *log_level* for *n* servers at once. Changing the
log level is explained in more detail at [alter server log level](../alter_server/log_level). Changing the
tee_pipe_name is explained in more detail at [alter server tee_pipe_name](../alter_server/tee_pipe_name).

### Syntax

    alter servers [where...] set <option>

### Example

    # Change the log-level to "debug"
    alter servers where uuid == 'f851c6a4-820e-11e5-9661-080027f37001' set log_level debug

---
title: "set log level"
weight: 81
---

With the argument *--log-level* it's possible to start with a certain log level.
The default log level is *info*. If you want the log level to change while
being online, this command can be used. It will *not* be saved when the server is
restarted.

Valid log levels are "debug", "info", "warning", "error" and "critical"

### Example

    # Change the log-level to "debug"
    alter server f851c6a4-820e-11e5-9661-080027f37001 set log_level debug

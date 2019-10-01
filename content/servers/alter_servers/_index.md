---
title: "alter servers"
date: 2019-09-27T15:48:59+02:00
weight: 2
---

Syntax:

    alter servers [where...] set log_level <option>

Valid options are *debug*, *info*, *warning*, *error* and *critical*.

This command will change the log level for *n* servers at once. Changing the
log level is explained in more detail at [alter server](../alter_server).

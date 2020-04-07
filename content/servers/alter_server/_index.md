---
title: "alter server"
weight: 58
---

Syntax:

    alter server <server_uuid / server_name> set <option>

Valid options are *address*, *port*, *backup_mode* and *log_level*. We can use
both, a servers name or uuid to change a server. To view the current servers
names and uuids use the command: `list servers name, uuid`

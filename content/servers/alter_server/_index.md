---
title: "alter server"
weight: 68
---

You can alter the *address*, *port*, *backup_mode*, *tee_pipe_name* and/or *log_level* of a server. You can use
both, a server's name or uuid to change a server. To view the current servers
names and uuids use the command: `list servers name, uuid`

### Syntax

    alter server <server_uuid / server_name> set <option>

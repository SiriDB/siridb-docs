---
title: "set backup mode"
weight: 84
---

When a backup_mode is enabled on a SiriDB server, all files in the database
directory will be closed (both dbpath and buffer_path). This way you can make
a backup of SiriDB without having problems with open files.

### Example

    # Enable the backup_mode
    alter server f851c6a4-820e-11e5-9661-080027f37001 set backup_mode true

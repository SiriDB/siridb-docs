---
title: "backup mode"
weight: 67
---

When a backup_mode is enabled on a SiriDB server, all files in the database
directory will be closed (both dbpath and buffer_path). This way you can make
a backup of SiriDB without having problems with open files.

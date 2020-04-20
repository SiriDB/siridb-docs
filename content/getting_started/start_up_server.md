---
title: "Start up server"
weight: 5
---

Now that SiriDB is installed and configured, you can start a SiriDB server:

```bash
$ siridb-server
```

If you use a configuration file instead of the environment variables and this file is stored at a different location than the default `/etc/siridb/siridb.conf`; you have to specify the path using the `-c/--config` argument:

```bash
$ siridb-server -c /my/path/siridb.conf
```

## Flag information

Flag | Description
----- | -----
`-h`, `--help` | Show the help message and exit.
`-c`, `--config CONFIG` | Define which SiriDB [configuration file](https://github.com/SiriDB/siridb-server/blob/master/siridb.conf) to use.
`-v`, `--version` | Show version information and exit.
`-l`, `--log-level` | Set initial log level: *debug*, *info*, *warning*, *error*, *critical*.
`--log-colorized` | Use colorized logging.

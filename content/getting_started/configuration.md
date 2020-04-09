---
title: "Configuration"
weight: 4
---

SiriDB can start with environment variables and/or with a configuration file. By default SiriDB will search for the configuration file in `/etc/siridb/siridb.conf` but alternatively you can specify a custom path by using the `-c/--config` argument.

```bash
$ siridb-server -c /my/path/siridb.conf
```
An example configuration file can be found here:
[https://github.com/SiriDB/siridb-server/blob/master/siridb.conf](https://github.com/SiriDB/siridb-server/blob/master/siridb.conf)


However be aware that the environment variables will overwrite the configuration file settings if both apply to the same setting.

Environmental variables:

Variable | Default | Description
-------- | ------- | -----------
`SIRIDB_SERVER_NAME` | ` %HOSTNAME:9010` | SiriDB will use this address:port for it's back-end connections. This must be an address that other servers can use to connect to. For example IPv4, IPv6 or a fqdn are all possible. When using IPv6 be sure to wrap the ip address with square brackets. For example [::1]:9010. The default value is %HOSTNAME:9010. The variable %HOSTNAME will be translate to the systems host name.
`SIRIDB_BIND_SERVER_ADDRESS` | `127.0.0.1` | Listen for SiriDB-server connections only on localhost. Use value 0.0.0.0 (or :: for IPv6) to bind to all interfaces.
`SIRIDB_LISTEN_CLIENT_PORT` | `9000` | SiriDB will listen for client connections on this port number.
`SIRIDB_BIND_CLIENT_ADDRESS` | `127.0.0.1` | Listen for client connections only on localhost. Use value 0.0.0.0 (or :: for IPv6) to bind to all interfaces.
`SIRIDB_IP_SUPPORT` | `ALL` | When ip_support is set to ALL, SiriDB will listen and connect to both IPv4 and IPv6 addresses. Valid options are ALL, IPV4ONLY and IPV6ONLY.
`SIRIDB_DEFAULT_DB_PATH` | `/var/lib/siridb` | SiriDB will load databases from, and create databases in this location.
`SIRIDB_OPTIMIZING_INTERVAL` | `3600` | SiriDB will run an optimize task each X seconds. A value of 0 (zero) disables optimizing.
`SIRIDB_HEARTBEAT_INTERVAL` | `30` | SiriDB uses a heart-beat interval to keep connections with other servers online.
`SIRIDB_BUFFER_SYNC_INTERVAL` | `0` | SiriDB can run fsync on the buffer file on an interval in milliseconds. This value is set to 0 by default which tells SiriDB to run fsync after each insert request. When having many insert requests per second, it can be useful to use an interval like 500 milliseconds.
`SIRIDB_MAX_OPEN_FILES` | `32768` | SiriDB will not open more shard files than max_open_files. Note that the total number of open files can be sligtly higher since SiriDB also needs a few other files to write to.
`SIRIDB_ENABLE_SHARD_COMPRESSION` | `1` | Use shard compression for storing data points. Set value 0 to disable shard compression.
`SIRIDB_ENABLE_PIPE_SUPPORT` | `0` | Enable named pipe support for client connections.
`SIRIDB_PIPE_CLIENT_NAME` | `siridb_client.sock` | SiriDB will bind the client named pipe in this location.
`HTTP_STATUS_PORT` | `0` | When the HTTP status port is not set (or 0), the service will not start. Otherwise the HTTP requests `/status`, `/ready` and `/healthy` are available which can be used for readiness and liveness requests. Example usage using wget: wget -q -O - http://siridb-server.local:8080/status
`SIRIDB_HTTP_API_PORT` | `0` | When the HTTP API port is not set (or 0), the API service will not start. Otherwise the HTTP POST requests can be user to insert or query data points.

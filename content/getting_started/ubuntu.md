---
title: "Ubuntu"
weight: 2
---

For Ubuntu we have a deb package available which can be downloaded [here](https://github.com/SiriDB/siridb-server/releases/latest).

Note: SiriDB requires *libexpat1*, *libuv1*, *libpcre2-8-0* and *libcleri0* these libraries can be easily installed using apt:
```
apt install libexpat1 libuv1 libpcre2-8-0 libcleri0
```

>Library `libcleri0` is available from Ubuntu 18.04, for older versions a deb package can be found here:
>https://github.com/transceptor-technology/libcleri/releases/latest

The .deb package installs a [configuration file](../configuration) at `/etc/siridb/siridb.conf`. You might want to view or change this file before starting SiriDB. See the section about [Configuration](../configuration).

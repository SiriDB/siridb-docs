---
title: "libsiridb (library)"
weight: 10
---

Libsiridb is a library which can be used to communicate
with [SiriDB](https://github.com/transceptor-technology/siridb-server) using
the C program language. This library contains useful functions but does not
handle the connection itself. When using
[libuv](http://libuv.org/) you should look at
[libsuv](https://github.com/SiriDB/libsuv#readme) which is a SiriDB
connector build on top of libuv and libsiridb.

### Installation

>Note: libsiridb requires [libqpack](https://github.com/transceptor-technology/libqpack)

Install debug or release version, in this example we will install the release version.
```
$ cd Release
```

Compile libsiridb
```
$ make all
```

Install libsiridb
```
$ sudo make install
```

> Note: run `sudo make uninstall` for removal.

### Quick usage

For an example you can look at [libsuv](https://github.com/SiriDB/libsuv#readme)
which contains a full example of how to use this library on top of libuv.

### More info

A more complete description of libsiridb can be found via the link below.

- https://github.com/SiriDB/libsiridb#readme
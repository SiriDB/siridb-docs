---
title: "Libsuv (C/C++)"
weight: 18
---

SiriDB Connector using [libuv](http://libuv.org/) and [libsiridb](./libsiridb).

### Installation


Install debug or release version, in this example we will install the release version.
```
$ cd Release
```

Compile libsuv
```
$ make all
```

Install libsuv
```
$ sudo make install
```

> Note: run `sudo make uninstall` for removal.

### Quick usage

Example to connect and authenticate to SiriDB:
```c
#include <suv.h>

uv_loop_t loop;

void connect_cb(siridb_req_t * req)
{
    suv_connect_t * connect = (suv_connect_t *) req->data;

    if (req->status) {
        printf("connect or auth failed: %s\n", siridb_strerror(req->status));
    } else if (req->pkg->tp != CprotoResAuthSuccess) {
        printf("authentication failed (error %u)\n", req->pkg->tp);
    } else {
        // do something with the connection
    }

    /* cleanup connetion handle */
    suv_connect_destroy(connect);

    /* lets stop the example */
    suv_close(suv_buf_from_req(req), NULL);

    /* cleanup connection request */
    siridb_req_destroy(req);
}

int main(void)
{
    struct sockaddr_in addr;
    /* initialize uv loop */
    uv_loop_init(&loop);

    /* asume siridb-server is running on localhost and port 9000 */
    uv_ip4_addr("127.0.0.1", 9000, &addr);

    /* create a siridb client */
    siridb_t * siridb = siridb_create();

    /* create a buffer for the connection */
    suv_buf_t * buf = suv_buf_create(siridb);

    /* create a connection request */
    siridb_req_t * req = siridb_req_create(siridb, connect_cb, NULL);

    /* create a connection handle */
    suv_connect_t * connect = suv_connect_create(req, "iris", "siri", "dbtest");

    /* explicit bind the connect handle to the request. (this must be done!) */
    req->data = (void *) connect;

    /* Warning: This overwrites tcp->data and siridb->data so do not use these
     *          members yourself. */
    suv_connect(&loop, connect, buf, (struct sockaddr *) &addr);

    /* run the uv event loop */
    uv_run(&loop, UV_RUN_DEFAULT);

    /* close the loop */
    uv_loop_close(&loop);

    /* cleanup buffer */
    suv_buf_destroy(buf);

    /* cleanup siridb */
    siridb_destroy(siridb);

    return 0;
}
```

### More info

A more complete description of libsuv can be found via the link below.

- https://github.com/SiriDB/libsuv#readme

---
title: "HTTP"
weight: 6
---

Before using the HTTP API, make sure at least one node has the HTTP API port enabled.
By default the API port is disabled, this can changed
with the `http_api_port` in the [configuration file](https://github.com/thingsdb/ThingsDB/blob/master/thingsdb.example.conf)
or with the `SIRIDB_HTTP_API_PORT` environment variable.

The API has support for [JSON](https://www.json.org) and can be used to perform queries.

## Headers

The header field `Content-Type` is required and needs `application/json`.

## Authentication

The HTTP API has supports for **basic** authentication: `--header 'Authorization: Basic c2E6c2lyaQ=='`.
The `Basic c2E6c2lyaQ==` stands for the default service account `sa` with password `siri` base64 encoded.

## URIs

The following URIs are available.

Service requests:

- /new-database
- /new-account
- /change-password
- /drop-account
- /new-pool
- /new-replica
- /drop-database
- /get-version
- /get-accounts
- /get-databases

Query request:
- /query/DBNAME

Insert request:
- /insert/DBNAME

## Examples

### Service request

Creating a new database using *curl* with *basic* authentication:

```bash
curl --location --request POST 'http://localhost:9020/new-database' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ==' \
--data-raw '{
	"dbname": "sampledb",
	"time_precision": "s",
	"buffer_size": 8192,
	"duration_num": "1w",
	"duration_log": "3d"
}'
```

> Possible response

```json
"OK"
```

### Query request

```bash
curl --location --request POST 'http://localhost:9020/query/dbtest' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic aXJpczpzaXJp' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"q": "select * from '\''aggr'\''",
	"t": "ms"
}'
```

An optional `{"t": "<TIME_PRECISION>"}` may be used, where `<TIME_PRECISION>` may be one of s, ms, us or ns. (seconds, milliseconds, microseconds or nanoseconds)
If it is not provided then the timestamp precision is set to the database default.


### Insert request

```bash
curl --location --request POST 'http://localhost:9020/insert/dbtest' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic aXJpczpzaXJp' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "my-example-serie": [
        [1578933215, 42],
        [1578933223, 123]
    ]
}'
---
title: "HTTP"
weight: 15
---

Before using the HTTP API, make sure at least one node has the HTTP API port enabled.
By default the API port is disabled, this can be changed
by setting `http_api_port` in the [configuration file](https://github.com/thingsdb/ThingsDB/blob/master/thingsdb.example.conf)
or by setting the `SIRIDB_HTTP_API_PORT` environment variable.

The API has support for both [JSON](https://www.json.org) and [qpack](https://github.com/cesbit/qpack) and can be used to perform service requests, inserts and queries.

## Headers

The header field `Content-Type` is required and needs `application/json` or `application/qpack`.

## Authentication

The HTTP API has supports for [basic authentication](https://en.wikipedia.org/wiki/Basic_access_authentication).

In the [examples](#examples) below we use the default service account `sa:siri` (`c2E6c2lyaQ==` when base64 encoded) and the default database user `iris:siri` (`aXJpczpzaXJp` when base64 encoded)

## URIs

The following URIs are available.

Service requests:

- [/new-database](#new-database)
- [/new-account](#new-account)
- [/change-password](#change-password)
- [/drop-account](#drop-account)
- [/new-pool](#new-pool)
- [/new-replica](#new-replica)
- [/drop-database](#drop-database)
- [/get-version](#get-version)
- [/get-accounts](#get-accounts)
- [/get-databases](#get-databases)

Query request:
- [/query/DBNAME](#query-request)

Insert request:
- [/insert/DBNAME](#insert-request)

## Examples

### Service request

Creating a new database using *curl* with *basic* authentication:

#### new-database
```bash
curl --location --request POST 'http://siridb-server-1:9020/new-database' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ==' \
--header 'Content-Type: text/plain' \
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

#### new-account

```bash
curl --location --request POST 'http://siridb-server-1:9020/new-account' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ==' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"account": "bob",
    "password": "passwd4bob"
}'
```
> Possible response

```json
    "OK"
```

#### change-password

```bash
curl --location --request POST 'http://siridb-server-1:9020/change-password' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ==' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"account": "bob",
    "password": "pass"
}'
```
> Possible response

```json
    "OK"
```

#### drop-account

```bash
curl --location --request POST 'http://siridb-server-1:9020/drop-account' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ==' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"account": "bob"
}'
```

> Possible response

```json
    "OK"
```

#### new-pool

```bash
curl --location --request POST 'http://siridb-server-3:9020/new-pool' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ==' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"dbname": "sampledb",
    "username": "iris",
    "password": "siri",
    "host": "siridb-server-1",
    "port": 9000
}'
```

> Possible response

```json
    "OK"
```

#### new-replica

```bash
curl --location --request POST 'http://siridb-server-2:9020/new-replica' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ==' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"dbname": "sampledb",
    "username": "iris",
    "password": "siri",
    "host": "siridb-server-1",
    "port": 9000,
    "pool": 0
}'
```

> Possible response

```json
    "OK"
```

#### drop-database

```bash
curl --location --request POST 'http://siridb-server-1:9020/drop-database' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ==' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"database": "sampledb",
    "ignore_offline": false
}'
```

> Possible response

```json
    "OK"
```

#### get-version

```bash
curl --location --request GET 'http://siridb-server-1:9020/get-version' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ=='
```

> Possible response

```json
    ["2.0.36"]
```

#### get-accounts

```bash
curl --location --request GET 'http://siridb-server-1:9020/get-accounts' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ=='
```

> Possible response

```json
    ["sa","bob"]
```

#### get-databases

```bash
curl --location --request GET 'http://siridb-server-1:9020/get-databases' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ=='
```

> Possible response

```json
    ["sampledb"]
```

### Query request

Selecting the number of points in a certain series called 'aggr'.

```bash
curl --location --request POST 'http://siridb-server-1:9020/query/dbtest' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic aXJpczpzaXJp' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"q": "select count() from '\''aggr'\''",
	"t": "ms"
}'
```

> Possible response

```json
    {"aggr":[
            [1588450390000,23]
        ]
    }
```

An optional `{"t": "<TIME_PRECISION>"}` may be used, where `<TIME_PRECISION>` can be s, ms, us or ns. (seconds, milliseconds, microseconds or nanoseconds).
If it is not provided then the timestamp precision is set to the database default.

### Insert request

Inserting two points in a series.

```bash
curl --location --request POST 'http://siridb-server-1:9020/insert/dbtest' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic aXJpczpzaXJp' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "my-example-serie": [
        [1578933215, 42],
        [1578933223, 123]
    ]
}'
```

> Possible response

```json
    {"success_msg":"Successfully inserted 2 point(s)."}
```

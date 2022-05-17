---
title: "Example database"
weight: 6
---

## Before we start...

Once at least one SiriDB server is running, you are ready to create your first SiriDB database.

Creating and managing SiriDB is done with a [Service account](http://localhost:1313/overview/service_account/). (Default **sa** with password **siri**)

SiriDB can listen to both a socket connection (`SIRIDB_LISTEN_CLIENT_PORT`) and, if _enabled_, to HTTP API  (`SIRIDB_HTTP_API_PORT`) requests.
For managing SiriDB with a socket connection, a [SiriDB Admin tool](https://github.com/SiriDB/siridb-admin) is created but in this example we assume that `SIRIDB_HTTP_API_PORT` is configured to port **9020**.

When creating a database there are a few options to keep in mind.

#### dbname

Name of the database. It is not possible to change the name of a database once it has been created.

#### time_precision
Each record in a time series database is called a point and each points consists of both a _value_ and a _time-stamp_. This _time-stamp_ can be in _seconds_ (`s`), _milliseconds_ (`ms`), _microseconds_ (`us`) or _nanoseconds_ (`ns`). Every point in a database is stored with the same time-precision so this precision needs to be defined while creating a new database.

*buffer_size*
For _integer_ and _float_ values, SiriDB uses a buffer before writing points to a shard. Every point in the buffer is also kept in memory thus the larger the buffer, the more memory is required. The chosen buffer size is the memory required in bytes for a single series. A buffer will only be created for series for series within the same pool. The buffer size will be set in `database.conf` and can be adjusted at some later time.

#### duration_num
SiriDB will eventually store points in shards. One shard contains points for a specific time window. The duration_num value is the default time window for numeric series. If a `SIRIDB_ENABLE_SHARD_AUTO_DURATION` is turned off, then this value will always be used. With auto duration on, SiriDB first tries to calculate an optimal time window for each series before sharding. A "good" duration value is should on average store approximately ~2000-10000 points in a shard. For example, if you expect ~5 minute samples, a value of `1w` (one week) is a good value. (7 (days) * 24 (hours) * 12 ()=2016).

#### duration_log
The same as duration_num, but for log values instead of numeric values. Since the behavior of log series might be significantly different it is possible to set a different shard duration for these values.

## Create a new database

With the knowledge from above in mind, we can create a database named `sampledb` using a second (`s`) time precision and an `8Kb` buffer size. We expect a one points at a minute interval to as a default we chose a `4d` interval for both our numeric and log values. In this example I'm using curl to make the HTTP request:

The authorization field contains `c2E6c2lyaQ==` which is the base64 encoding for `sa:siri`, the default service account.


```
curl --location --request POST 'http://localhost:9020/new-database' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic c2E6c2lyaQ==' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"dbname": "sampledb",
	"time_precision": "s",
	"buffer_size": 8192,
	"duration_num": "4d",
	"duration_log": "4d"
}'
```

If everything when fine, you should have received a message "OK".

## Insert data

The database now is empty. Time series will be created automatically when inserting data. The type of the time series will be defined by the first point by looking at the value.

In this example we just insert a single series with 20 data points with integer values.

The authorization field contains `aXJpczpzaXJp` which is the base64 encoding for `iris:siri`, the default database user.

```
curl --location --request POST 'http://localhost:9020/insert/sampledb' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic aXJpczpzaXJp' \
--header 'Content-Type: text/plain' \
--data-raw '{
    "my-series": [
        [1652704834, 93],
        [1652704894, 14],
        [1652704954, 46],
        [1652705014, 42],
        [1652705074, 21],
        [1652705134, 80],
        [1652705194, 3],
        [1652705254, 46],
        [1652705314, 29],
        [1652705374, 23],
        [1652705434, 17],
        [1652705494, 32],
        [1652705554, 79],
        [1652705614, 3],
        [1652705674, 14],
        [1652705734, 65],
        [1652705794, 98],
        [1652705854, 32],
        [1652705914, 38],
        [1652705974, 29]
    ]
}'
```

> Note that this example contains perfectly ordered points but this is not required for SiriDB.

You should receive a JSON response:

```json
{"success_msg":"Successfully inserted 20 point(s)."}
```

## Query data

Perform a query to see if we can get any data back. The following query should return the last 10 points from our time series.

```
curl --location --request POST 'http://localhost:9020/query/sampledb' \
--header 'Content-Type: application/json' \
--header 'Authorization: Basic aXJpczpzaXJp' \
--header 'Content-Type: text/plain' \
--data-raw '{
	"q": "select * from '\''my-series'\'' tail 10"
}'
```

```json
{"my-series":[[1652705434,17],[1652705494,32],[1652705554,79],[1652705614,3],[1652705674,14],[1652705734,65],[1652705794,98],[1652705854,32],[1652705914,38],[1652705974,29]]}
```

## More

With the HTTP API you can also change passwords, create new accounts, expand a SiriDB cluster across multiple pools, add replica's and more.

Visit the [documentation HTTP API site](https://docs.siridb.net/connect/http_api/) for more information.

Besides the HTTP API, you can also look at [native connectors](https://docs.siridb.net/connect/), especially for fast inserting and querying data this can be useful.

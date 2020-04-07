---
title: "python"
weight: 7
---


The SiriDB Connector is a self-contained Python driver for communicating with SiriDB servers.
This manual describes how to install and configure SiriDB Connector for Python 3, and how to use it to develop database applications.

### Installation

From PyPI (recommended)

```
pip install siridb-connector
```

From source code

```
python setup.py install
```

### Quick usage

```python
import asyncio
import time
import random
from siridb.connector import SiriDBClient

async def example(siri):
    # Start connecting to SiriDB.
    # .connect() returns a list of all connections referring to the supplied
    # hostlist. The list can contain exceptions in case a connection could not
    # be made.
    await siri.connect()

    try:
        # insert
        ts = int(time.time())
        value = random.random()
        await siri.insert({'some_measurement': [[ts, value]]})

        # query
        resp = await siri.query('select * from "some_measurement"')
        print(resp)

    finally:
        # Close all SiriDB connections.
        siri.close()


siri = SiriDBClient(
    username='iris',
    password='siri',
    dbname='dbtest',
    hostlist=[('localhost', 9000)],  # Multiple connections are supported
    keepalive=True)

loop = asyncio.get_event_loop()
loop.run_until_complete(example(siri))
```

### More info

A more complete description of the python-connector can be found via the link below.

- https://github.com/SiriDB/siridb-connector#readme

---
title: "set tee pipe name"
weight: 85
---

Some projects like [Enodo project](../../../related_projects/enodo) may benefit from receiving all SiriDB data. Because these projects usually experience the same scaling problems as SiriDB does, we have chosen to support a *tee* option on each SiriDB server.
Using this feature makes it possible to install a service on at least one SiriDB server in each pool. Such a service should install a UNIX Pipe server which accepts SiriDB data in [QPack](https://github.com/transceptor-technology/qpack) format.

SiriDB will then try to connect to the pipe, and once a connection is established, all SiriDB data points with the SiriDB pool as target, will be forwarded to the pipe.

A package send to the pipe will have a header like:

```none
┌───────────┬───────────┬───────────┬───────────┬───────────┐
│ LEN (4)   │ ID (2)    │ TYPE (1)  │ CHK (1)   │ DATA (..) │
└───────────┴───────────┴───────────┴───────────┴───────────┘
```

Field  | Description
-------|----------------
`LEN`  | Length of the *data*, stored as **Unsigned, 32-bit, Little Endian**. The header size is *not* included in the length.
`ID`   | Can be ignored
`TYPE` | Can be ignored
`DATA` | Contains the actual data points in QPack format.

The data is packed like:

```none
{
    'serie-name': [[<TIMESTAMP>, <VALUE>], ...],
    ...
}
```

If you like to disable the `tee`, then use `false` instead of a string.

### Example

    # Change the log-level to "debug"
    alter server f851c6a4-820e-11e5-9661-080027f37001 set tee_pipe_name '/tmp/data.sock'

---
title: "set tee"
weight: 108
---

Some projects like [Enodo project](../../../related_projects/enodo) may benefit from receiving all SiriDB data. Because these projects usually experience the same scaling problems as SiriDB does, we have chosen to support a *tee* option on each SiriDB server.

Once a tee is configured, SiriDB will try to connect to the tee, and once a connection is established, all SiriDB data points will be forwarded to the tee. Note that each SiriDB server in a cluster must be able to access the tee.

A package send to the tee will have a header like:

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

    # Configure a tee, in this example enodo.listener.local
    alter database set tee 'enodo.listener.local'

    # Disable the tee
    alter database set tee false

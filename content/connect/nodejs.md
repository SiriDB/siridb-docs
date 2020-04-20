---
title: "Node.js"
weight: 20
---


Node.js add-on (C++) for SiriDB.

### Installation

```
node-gyp configure && node-gyp build
```

### Quick usage

```javascript
const sdbaddon = require('./build/Release/siridb');

var siridb = new sdbaddon.SiriDBClient(
    "iris",         // database user
    "siri",         // password
    "dbtest",       // database name
    "localhost",    // server address
    9000            // server port
);

siridb.connect(err => {
    // success: err is null
    // error:   err is a string with an error message
    if (err) {
        console.error(`Connection error: ${err}`);
    } else {
        siridb.close();
    }
});
```

### More info

A more complete description of the node.js add-on can be found via the link below.

- https://github.com/SiriDB/siridb-nodejs-addon#readme

---
title: "Java"
weight: 21
---

The SiriDB Connector for Java is a self-contained Java driver for communicating with SiriDB servers.

### Installation

First you need to install the [Java-QPack](https://github.com/transceptor-technology/java-qpack) library. Add this library to your project.

Now you can install the connector. You can get a copy of the compiled jar file [here](https://github.com/SiriDB/java-siridb-connector/releases/latest) or clone the [repository](https://github.com/SiriDB/java-siridb-connector) and compile the code. Add the jar file as library to your project.

### Quick usage

The SiriDB Connector can be used to communicate with a single SiriDB server and a more advanced client is provided which can connect to multiple SiriDB servers so queries and inserts are balanced.

An example of how to create a Client can be found below.

```Java
hostlist = new String[][]{
    {"localhost", "9000", "-1"},
    {"localhost", "9001", "5"},
    {"localhost", "9002", "1"},
    {"localhost", "9003", "2"}
};

client = new Client("iris", "siri", "test", hostlist, true);
```

### More info

A more complete description of the java-connector can be found via the link below.

- https://github.com/SiriDB/java-siridb-connector#readme

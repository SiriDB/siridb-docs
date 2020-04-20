---
title: "Golang"
weight: 17
---

A SiriDB-Connector for the Go language

### Installation

Install the package to your [$GOPATH](https://github.com/golang/go/wiki/GOPATH "GOPATH") with the [go tool](https://golang.org/cmd/go/ "go command") from shell:
```bash
$ go get github.com/SiriDB/go-siridb-connector
```
Make sure [Git is installed](https://git-scm.com/downloads) on your machine and in your system's `PATH`.

### Quick usage

_Go SiriDB Connector_ can be used to communicate with a single SiriDB server and a more advanced client is provided which can connect to multiple SiriDB servers so queries and inserts are balanced.

#### Single connection
This is some example code for how to use the Go-SiriDB-Connector as a single connection.
```go
package main

import (
	"fmt"

	"github.com/SiriDB/go-siridb-connector"
)

func example(conn *siridb.Connection, ok chan bool) {
	// make sure the connection will be closed
	defer conn.Close()

	// create a new database with the following configuration
	options := make(map[string]interface{})
	options["dbname"] = "dbtest"
	options["time_precision"] = "s"
	options["buffer_size"] = 1024
	options["duration_num"] = "1w"
	options["duration_log"] = "1d"

	// using the default service account 'sa' and password 'siri'
	if res, err := conn.Manage("sa", "siri", siridb.AdminNewDatabase, options); err == nil {
		fmt.Printf("Manage result: %v\n", res)
	}

	// connect to database 'dbtest' using user 'iris' and password 'siri'
	// this is an example but usually you should do some error handling...
	if err := conn.Connect("iris", "siri", "dbtest"); err == nil {

		seriename := "serie-001"
		timestamp := 1471254705
		value := 1.5
		serie := make(map[string][][]interface{})
		serie[seriename] = [][]interface{}{{timestamp, value}}

		// insert data
		if res, err := conn.Insert(serie, 10); err == nil {
			fmt.Printf("Insert result: %s\n", res)
		}

		// perform a query
		if res, err := conn.Query("select * from *", 10); err == nil {
			fmt.Printf("Query result: %v\n", res)
		}
	}

	// send to the channel
	ok <- true
}

func main() {
	// create a new connection
	conn := siridb.NewConnection("localhost", 9000)

	// a connection will send output to stdout except when a log channel is used.
	// setup a log channel using:
	//  	conn.LogCh = myLogChannel

	// create a channel
	ok := make(chan bool)

	// run the example
	go example(conn, ok)

	// wait for the channel
	<-ok
}

```

#### SiriDB client
And one example for using the client. A client can be used for connecting to multiple SiriDB servers. Queries and inserts will be send to a random SiriDB server. When a connection is lost, it will retry to setup the connection each 30 seconds.
```go
package main

import (
	"fmt"

	"github.com/SiriDB/go-siridb-connector"
)

func example(client *siridb.Client, ok chan bool) {
	// make sure the connection will be closed
	defer client.Close()

	client.Connect()

	// IsConnected() returns true if at least one server is connected.
	// Failed connections will retry creating a connection each 30 seconds.
	if client.IsConnected() {
		if res, err := client.Query("list series", 2); err == nil {
			fmt.Printf("Query result: %s\n", res)
		}
	} else {
		fmt.Println("not even a single server is connected...")
	}

	// send to the channel
	ok <- true
}

func main() {
	// create a new client
	client := siridb.NewClient(
		"iris",   // username
		"siri",   // password
		"dbtest", // database
		[][]interface{}{
			{"server1", 9000},
			{"server2", 9000},
		}, // siridb server(s)
		nil, // optional log channel
	)

	// create a channel
	ok := make(chan bool)

	// run the example
	go example(client, ok)

	// wait for the channel
	<-ok
}
```

### More info

A more complete description of the go-connector can be found via the link below.

- https://github.com/SiriDB/go-siridb-connector#readme
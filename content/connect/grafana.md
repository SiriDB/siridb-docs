---
title: "Grafana SiriDB HTTP datasource"
weight: 16
---

A SiriDB data source plugin for Grafana.

### Installation

Go to the Grafana plugins folder. (usually this is /var/lib/grafana/plugins/)

```
cd /var/lib/grafana/plugins/
```

Clone the git project into the plugins folder:
```
git clone https://github.com/SiriDB/grafana-siridb-http-datasource.git
```

Restart Grafana
```
sudo systemctl restart grafana-server.service
```

### Quick usage
See the following blog article on how to configure and use this plugin: https://github.com/SiriDB/grafana-siridb-http-example.


### More info

A more complete description of the SiriDB data source plugin for Grafana can be found via the link below.

- https://github.com/SiriDB/grafana-siridb-http-datasource#readme

>**Note**:
>
>Since SiriDB version 2.0.36 and Grafana-Sirdb-HTTP-datasource version ... you can use the build-in HTTP API instead of the [SiriDB http connector](https://github.com/SiriDB/siridb-http).
>In this case you only need to provide URL: https://localhost:9020/query/dbname when you add a data source in Grafana.
>If you still wish to use the SiriDB HTTP connector you have to configure and start the SiriDB HTTP service and you need to enter the URL:https://localhost:5050/query when adding the data source to Grafana.

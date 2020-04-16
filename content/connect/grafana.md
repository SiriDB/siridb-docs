---
title: "Grafana SiriDB HTTP datasource"
weight: 15
---

A SiriDB data source plugin for Grafana.

### Requirements
SiriDB HTTP is required for this plugin. If you do not have a SiriDB HTTP instance running then
it might be a good choice to install SiriDB HTTP on your Grafana server.

[https://github.com/SiriDB/siridb-http](https://github.com/SiriDB/siridb-http#readme)

Make sure to configure SiriDB HTTP to allow Basic Authentication. Optionally you can also choose
to disable authentication.

>Note: at least SiriDB server version 2.0.14 is required since this plugin makes use of the
>limit aggregation function.


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
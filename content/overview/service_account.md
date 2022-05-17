---
title: "Service account"
weight: 8
---

Service accounts are used for managing databases. A service account is a user on a SiriDB server, which should not be confused with a [database user](../database_user). A service account has no access to a SiriDB database. The reason for separating these accounts is that a database can extend over multiple servers, while a service account only gives access to a single server.

You can manage the service account(s) and database(s) via the [SiriDB Admin tool](https://github.com/SiriDB/siridb-admin) or using the [HTTP API](../../connect/http_api).

Every SiriDB server has already one default service account installed:  **sa** user with password **siri**.

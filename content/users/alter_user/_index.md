---
title: "alter user"
date: 2019-09-27T15:51:49+02:00
weight: 4
---

Syntax:

	alter user 'username' set <option>

Valid options are *password* and *name*.

Change a user name or password.

Example:

	# Change the password for "iris" to "siri"
	alter user 'iris' set password 'siri'

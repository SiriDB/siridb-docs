---
title: "grant access"
date: 2019-09-27T15:50:08+02:00
weight: 2
---

Syntax:

	grant <access> to user 'username'

Grants access rights to a user. For information about access rights
see [access rights](../access_rights).

Example:

	# Grant drop and create to user "iris"
	grant drop, create to user "iris"


Output:

	{"success_msg": "Successfully granted permissions to user ..."}

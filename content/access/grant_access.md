---
title: "grant access"
weight: 100
---

Grants access rights to a user. For information about access rights
see [access rights](../access_rights).

### Syntax

	grant <access> to user 'username'

### Example

	# Grant drop and create to user "iris"
	grant drop, create to user "iris"


Output:

	{"success_msg": "Successfully granted permissions to user ..."}

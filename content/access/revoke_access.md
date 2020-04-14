---
title: "revoke access"
weight: 100
---

Revokes access rights from a user. For information about access rights
see [access rights](../access_rights).

>**Warning**
>
>If accidentally all access rights for all users are gone, you need to recover
>the default user. See [restore access](../restore_access) for how to recover from such a situation.

### Syntax

	revoke <access> from 'username'

### Example

	# Revoke drop and create from user "iris"
	revoke drop, create from user "iris"


Output:

	{"success_msg": "Successfully revoked permissions from ..."}
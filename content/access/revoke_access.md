---
title: "revoke access"
weight: 89
---

Syntax:

	revoke <access> from 'username'

Revokes access rights from a user. For information about access rights
see [access rights](../access_rights).

>**Warning**
>
>If accidentally all access rights for all users are gone, you need to recover
>the default user. See [no access](../no_access) for how to recover from a situation
>not having access to SiriDB.

Example:

	# Revoke drop and create from user "iris"
	revoke drop, create from user "iris"


Output:

	{"success_msg": "Successfully revoked permissions from ..."}
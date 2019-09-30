---
title: "list users"
date: 2019-09-27T15:51:42+02:00
weight: 3
---

Syntax:

	list users [columns] [where ...] [limit ...]

columns
-------
Valid columns are:

- name: User name.
- access: Access rights assigned to the user.

When no columns are provided the default is used. (name, access)

Example:

	# List all users
	list users

	# List users with full access
	list users where access == full

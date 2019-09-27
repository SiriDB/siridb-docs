---
title: "count users"
date: 2019-09-27T15:51:34+02:00
weight: 2
---

Syntax:

	count users [where ...]

Count users returns the number of users.

Examples:

	# Get number of users
	count users

	# Get number of users not equal to 'iris'
	count users where name != 'iris'

Example output:

	{"users": 6}

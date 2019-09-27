---
title: "count groups"
date: 2019-09-27T15:47:32+02:00
weight: 2
---

Syntax:

	count groups [where ...]

Count groups returns the number of groups defined in the database.

Example:

	# Get number of groups
	count groups

	# Get number of groups with more than 100 series
	count groups where series > 100

Example output:

	{"groups": 23}
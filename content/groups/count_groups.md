---
title: "count groups"
weight: 60
---

Count groups returns the number of groups defined in the database.

### Syntax

	count groups [where ...]

### Examples

	# Get number of groups
	count groups

	# Get number of groups with more than 100 series
	count groups where series > 100

Example output:

	{"groups": 23}
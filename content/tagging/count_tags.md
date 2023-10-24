---
title: "count tags"
weight: 75
---

Count tags returns the number of tags defined in the database.

### Syntax

	count tags [where ...]

### Examples

	# Get number of tags
	count tags

	# Get number of tags with more than 100 series
	count tags where series > 100

Example output:

	{"tags": 23}

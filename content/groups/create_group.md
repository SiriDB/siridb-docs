---
title: "create group"
weight: 59
---

Groups should be between **backticks** to make them different from strings.
Since a group is basically a cached regular expression we need to provide
the regular expression we want to use for the group.


### Syntax

	create group `groupname` for /regular_expression/

### Example

	# Create a group linux
	create group `linux` for /linux.*/

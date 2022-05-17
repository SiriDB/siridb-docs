---
title: "set expression"
weight: 70
---

Change the regular expression for a group.

### Examples

	# Create group `linux`
	create group `linux` for /linux.*/

	# Change expression so we will match case insensitive
	alter group `linux` set expression /linux.*/i

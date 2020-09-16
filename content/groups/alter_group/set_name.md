---
title: "set name"
weight: 70
---

Change the name for a group.

>**Note**
>
>This statement expects a normal string using single or double quotes.
>The reason is that 'set name' expects a string and not a group.

### Example

	# Rename group `linux` to `ubuntu`
	alter group `linux` set name 'ubuntu'

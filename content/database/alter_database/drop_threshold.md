---
title: "drop threshold"
weight: 102
---

This value is used to protect you from accidentally dropping data from SiriDB.
The threshold is a value between 0 and 1 (0/100%). The threshold value is only
checked against the pool receiving your query. The default threshold value is
1 (100%) but it might be a good idea to change this to a lower value.

>**Note**
>
>Currently the drop_threshold is only used for dropping series and shards
>because these are the only queries where we allow to drop multiple
>entries at once.

### Examples

	# Do not allow dropping more than 10% series or shards at once
	alter database set drop_threshold 0.1

	# View the current threshold
	show drop_threshold

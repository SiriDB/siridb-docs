---
title: "columns"
weight: 73
---

Valid columns are:

- name: Tag name
- series: Number of series in the tag.

When no columns are provided the default is used. (name)

### Examples

	# View all tags
	list tags

	# View tags and the number of series tagged
	list tags name, series

	# sample output (list tags)
	{
		"columns": ["name", "series"],
		"tags": [
			["linux", 52042],
			["windows", 7]
        ]
    }

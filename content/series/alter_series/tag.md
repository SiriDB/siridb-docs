---
title: "tag"
weight: 57
---


### Examples

	# Tag series
	alter series 'my-series-001', 'my-series-002' tag `my-series`

    # Another tag example
    alter series /linux.*/ where type == float tag `linux-float`

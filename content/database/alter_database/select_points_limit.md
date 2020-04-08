---
title: "select points limit"
weight: 82
---

Change the maximum points which can be returned by a select query. The default and recommended value is set to one million points. This value is chosen to prevent a single query for taking to much memory and ensures SiriDB can respond to almost any query in a reasonable amount of time.

Example:

    # Increase the select points limit to 5 million
    alter database set select_points_limit 5000000
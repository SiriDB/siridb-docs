---
title: "count users"
weight: 92
---

Count users returns the number of users.

### Syntax

    count users [where ...]

### Examples

    # Get number of users
    count users

    # Get number of users not equal to 'iris'
    count users where name != 'iris'

Example output:

    {"users": 6}

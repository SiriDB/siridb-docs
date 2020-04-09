---
title: "columns"
weight: 79
---

Valid columns are:

- name: User name.
- access: Access rights assigned to the user.

When no columns are provided the default is used. (name, access)

Example:

    # List all users
    list users

    # List users with full access
    list users where access == full

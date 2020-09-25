---
title: "create user"
weight: 95
---

Create a new user. This will create a new user without access to SiriDB.
For more information on how to grant access to a user see [grant access](../../access/grant_access).

### Syntax

    create user 'my-username' set password 'my-password'

### Examples

    # This will create a new user 'iris' with password 'siri'
    create user 'iris' set password 'siri'

    # Grant "read" access to "iris"
    grant read to user "iris"

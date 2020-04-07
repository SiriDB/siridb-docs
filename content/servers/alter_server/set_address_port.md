---
title: "set address/port"
weight: 61
---

Usually its not required to change the servers address or port using this
command but instead you should change the address/port in the configuration
file (default /etc/siridb/siridb.conf). When the server gets online it will
contact all SiriDB servers and they will automatically update to the new
address/port in their local database. However, if all servers in a cluster are
updated at once, we need to tell at least one SiriDB server where to find the
other server(s). This should be the only situation when this command is
required.

Example:

    # srv1 and srv2 both have changed to another address so
    # they are not able find each other. The command below
    # is executed on srv1 and tells where to find srv2.

    alter server 'srv2.old.domain:9010' set address 'srv2.new.domain'

    # After executing the above command, srv1 will connect to srv2
    # using the new domain name and announces its own new address so
    # srv2 will update the address automatically and will connect
    # to srv1 again.

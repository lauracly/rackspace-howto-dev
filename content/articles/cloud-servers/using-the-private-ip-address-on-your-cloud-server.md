---
node_id: 149
title: Using the Private IP Address on your Cloud Server
type: article
created_date: '2011-03-15'
created_by: Rackspace Support
last_modified_date: '2015-08-20'
last_modified_by: Kyle Laffoon
product: Cloud Servers
body_format: tinymce
---

Each Cloud Server comes with two addresses that are available for your
use. One address is an external &rdquo;real-world&rdquo; IP address that is
accessible from the Internet and the other is an internal or "private"
IP address.  This internal IP address is on a network commonly called
ServiceNet and is used within the Cloud.

<div>

#### Why do Cloud Servers have an Internal IP Address?

</div>

This IP address is an internal address that is only accessible by the
Cloud Server platforms because it allows you to transfer data between
Cloud Servers with no bandwidth charges.

<div>

#### Is ServiceNet Free?

</div>

Yes! This is a standard service that is offered with each Cloud Server
at no additional cost. Your Cloud Server is pre-configured with your
private IP address as soon as it is built.

<div>

#### How Do I Find My Private IP Address?

If you log into your Cloud Server, via SSH or the Console, you can type
the command ip addr show eth1on most distributions to find your private
IP address. Then look for the inet addrline. A sample output is posted
here:

</div>

<div>

        # ip addr show eth1

        eth1      Link encap:Ethernet  HWaddr 00:18:78:56:34:12
        ; inet addr:10.1.98.200  Bcast:10.1.98.255  Mask:255.255.255.0

\*\*\*\* You will need the address on the second line next to 'inet
addr:'.

</div>

<div>

#### What can I use the private address for?

The private IP address has many uses:

</div>

-   High-availability Heartbeat
-   Load balancing
-   Remote database connections
-   NFS/rsync
-   Remote backup

As you can see, the possibilities are endless!


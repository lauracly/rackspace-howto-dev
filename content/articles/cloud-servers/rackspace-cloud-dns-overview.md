---
node_id: 1231
title: Rackspace Cloud DNS - Overview
type: article
created_date: '2011-10-19 21:05:34'
created_by: RackKCAdmin
last_modified_date: '2015-12-23 16:1610'
last_modified_by: kyle.laffoon
product: Cloud Servers
body_format: tinymce
---

### Prerequisites

[Rackspace Cloud
DNS:](https://www.rackspace.com/knowledge_center/article/rackspace-cloud-dns)

**Cloud DNS Overview**

Our existing DNS infrastructure is a Globally Distributed Anycast
Network. Rackspace currently has DNS servers located in Texas, Virginia,
and London. Within each datacenter, we have our nameservers split up so
that we have no single point of failure in front of our DNS servers.

![](http://c777730.r30.cf2.rackcdn.com/dnsoverview.png)

Using anycast, we broadcast IP addresses from each location, which gives
us two advantages:

1.  The DNS queries will generally go to the geographically closest
    nameservers. This gives faster results no matter where the queries
    originate. 
2.  If an entire datacenter were to fail, or even if all of the DNS
    servers within a specific datacenter were to fail, the DNS queries
    will automatically start going to the next best location. 

### Next steps

**[Rackspace Cloud DNS - Available
Features](https://admin.rackspace.com/knowledge_center/cloud_dns_available_features)**

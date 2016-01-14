---
node_id: 1388
title: Rackspace Cloud Essentials - Choosing the right-size cloud server
type: article
created_date: '2012-05-02 18:02:52'
created_by: RackKCAdmin
last_modified_date: '2015-12-31 18:3731'
last_modified_by: stephanie.fillmon
product: Cloud Servers
body_format: tinymce
---

One of the great advantages of using Rackspace Cloud Servers ([product
page](http://www.rackspace.com/cloud/servers/)) is the flexibility that
you have to purchase only the amount of computing power you need.  When
business is good and you need increased server capacity, you can scale
your implementation horizontally by distributing your traffic over
multiple servers by using Cloud Load Balancers ([product
page](http://www.rackspace.com/cloud/load-balancing)).

#### So, the question is, *how much computing power do you need?* {.p1}

One way to answer this question is to install and test your application
on a few different-size implementations.  Then, perform load testing of
your application while simulating traffic to your site.  It is best to
test your site from a URL that does more than just retrieve a static web
page; for example, access a page that uses PHP and makes a database
query, so the test is more representative of normal traffic.   

This article shows some of the standard tools for viewing your server's
performance, and helps you determine whether the server size that you
chose is up to the task.

#### Considerations {.p1}

One thing to consider is that Rackspace Cloud Servers are virtual
partitions of larger physical machines that allocate resources based on
a process called CPU scheduling.  They do not perform exactly like a
dedicated machine with similar resources. You can find out more details
about CPU scheduling by reading the Performance section of our [Cloud
Servers
FAQ](http://www.rackspace.com/knowledge_center/product-faq/cloud-servers).

OnMetal Cloud Servers ([product
page](http://www.rackspace.com/cloud/servers/onmetal)) are also
available. OnMetal servers are single-tenant, bare metal servers
provisioned via the same OpenStack API as our cloud server. They can be
created or deleted as quickly as VMs to offer the agility of
multi-tenant environments with the performance of single-tenant
hardware.

Also consider that cloud servers come in various flavors or server types
including: General Purpose Compute optimized, Memory-optimized, and I/O
optimized servers. The Memory, Compute, and I/O flavors offer faster
disk access and network speed than General Purpose flavors. Disk size
and virtual CPU allocation are different for equivalent flavors. Compare
the offerings based on the performance needs that you identify in the
following sections.

**Flavor classes for different workloads**

+--------------------------+--------------------------+--------------------------+
| (Prototype)              | (Scale)                  | (Optimize)               |
+--------------------------+--------------------------+--------------------------+
| **General purpose\       | **Workload-optimized\    | **Workload-optimized\    |
|  vitual servers**        |  virtual servers**       |  OnMetal servers**       |
+--------------------------+--------------------------+--------------------------+
|                          | **Description**          |                          |
+--------------------------+--------------------------+--------------------------+
| VMs running on           | VMs running on           | API-driven, instantly    |
| multi-tenant hosts.\     | multi-tenant hosts.\     | provisioned,\            |
|  Smaller sizes, balanced |  Smaller sizes and       |  single-tenant,          |
| resources, and\          | workload-specific\       | bare-metal servers.\     |
|  CPU and network burst   |  designs allow for       |  Full host and           |
| capability\              | price-performance\       | workload-specific\       |
|  provide lowest price    |  optimization for your   |  designs provide         |
| points and best\         | particular\              | large-scale cost\        |
|  value.                  |  application.            |  efficiencies as  well   |
|                          |                          | as maximum and           |
|                          |                          | consistent performance.  |
+--------------------------+--------------------------+--------------------------+
| **General purpose**      | **Workload optimized**   | **Workload optimized**   |
+--------------------------+--------------------------+--------------------------+
| Class name: **General    | Class name: **Compute    | Class name: **OnMetal    |
| Purpose v1  \            | v1**                     | Compute**                |
|                     and  |                          |                          |
| Standard**               |                          |                          |
+--------------------------+--------------------------+--------------------------+
| Use cases:               | Use cases:               | Use cases:               |
| -   Test and development |                          |                          |
| -   Low- to              | -   Medim- to            | -   Large-traffic web    |
|     medium-traffic web   |     large-traffic web    |     servers, application |
|     servers              |     servers, application |     servers, batch       |
| -   Batch processing     |     servers, batch       |     processing, and      |
| -   Network appliances   |     processing, and      |     network appliances   |
| -   Small to medium      |     network appliances   |                          |
|     databases            |                          |                          |
+--------------------------+--------------------------+--------------------------+
|                          | **I/O optimized**        | **I/O optimized**        |
+--------------------------+--------------------------+--------------------------+
|                          | Class name: **I/O v1**   | Class name: **OnMetal    |
|                          |                          | I/O**                    |
+--------------------------+--------------------------+--------------------------+
|                          | Use cases:               | Use cases:               |
|                          | -   Medium to large      | -   Large-scale online   |
|                          |     relational databases |     transaction          |
|                          |     and NoSQL data       |     processing (OLTP),   |
|                          |     stores               |     relational           |
|                          |                          |     databases, and NoSQK |
|                          |                          |     data stores          |
+--------------------------+--------------------------+--------------------------+
|                          | **Memory optimized**     | **Memory optimized**     |
+--------------------------+--------------------------+--------------------------+
|                          | Class name: **Memory     | Class name: **OnMetal    |
|                          | v1**                     | Memory**                 |
+--------------------------+--------------------------+--------------------------+
|                          | Use cases:               | Use cases:               |
|                          | -   Medium to large      | -   Large caches, search |
|                          |     caches, search       |     indexes, and         |
|                          |     indexes, and         |     in-memory analytics  |
|                          |     in-memory analytics  |                          |
+--------------------------+--------------------------+--------------------------+

### Performance testing in Linux {.p1}

If your application is running on a Linux system, there are many
utilities that you can use to determine how well your server is handling
the load.  The main statistics you should examine are the **load
average** on the server and the **available memory** while your
application is running.

**free**: This is a quick and easy monitoring utility that gives you a
snapshot view of the amount of available memory on your server. Adding
the -m switch to the command shows you available memory in megabytes (as
opposed to the default kilobytes). 

![](http://c14994050.r50.cf2.rackcdn.com/free-m.png)

 

**Top**: This utility is useful for more than just checking available
memory.  You can also view the load average on the server, and the
processes that are using the most resources on your server. 

![](http://c14994050.r50.cf2.rackcdn.com/top.png)

 

**iotop**: You can use the 'iotop' command to monitor disk I/O on a
per-process basis.

![](/knowledge_center/sites/default/files/field/image/2013-08-08_1232.png)

**dstat**: The `dstat` command also shows you the I/O statistics and
other information with more versatility than other commands, in terms of
reporting. 

![](http://c14994050.r50.cf2.rackcdn.com/dstat.png)

Both iotop and dstat might require extra packages to be installed on
your server.

If you use these tools while running your web application and you see an
excessive load average or excessive memory usage, you need to tune
either your application or choose a more powerful server flavor on which
to run it.  Following are some other tools that you can use to benchmark
and monitor your servers and applications.

### Resources for testing your system {.p1}

**apache "mod\_status" module** - Use this module with Apache to see how
many connections are being used, and how you might need to change its
setup.  [Read the detailed
article](http://articles.slicehost.com/2010/3/26/enabling-and-using-apache-s-mod_status-overview)
on the apache mod\_status module.

[**ApacheBench**](http://httpd.apache.org/docs/2.0/programs/ab.html) -
This HTTP load generating tool reports how many requests per second your
application can process.

**[Apache JMeter](http://jmeter.apache.org/)** - provides load testing
and performance monitoring for web applications.

**[Munin](http://munin-monitoring.org/)** - This monitoring system
enables you to see your server statistics through a web interface.

 

### Additional resources:  Scaling, tuning, and load balancing {.p1}

Article:  [Scaling for the Holidays - To Scale Vertically or
Horizontally?](http://www.rackspace.com/blog/scaling-for-the-holidays-part-1-to-scale-vertically-or-horizontally/)

Article:  [Scaling for the Holidays - Take Advantage of
Caching](http://www.rackspace.com/blog/scaling-for-the-holiday-series-part-2-take-advantage-of-caching/%20)

Article: [Scaling for the Holidays - Web Server
Tuning](http://www.rackspace.com/blog/holiday-scaling-web-server-tuning/)

Article: [Scaling for the Holidays - Load
Balancers](http://www.rackspace.com/blog/scaling-for-the-holidays-part-4-load-balancers/%20)

 

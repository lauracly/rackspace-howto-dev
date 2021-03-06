---
node_id: 365
title: Linux Patching for Cloud Servers Managed Operations Service Level
type: article
created_date: '2011-04-04'
created_by: Rackspace Support
last_modified_date: '2016-01-13'
last_modified_by: Nate Archer
product: Managed Operations
body_format: markdown_w_tinymce
---

Linux patching comes directly from vendors or distribution communities. The exception is Red Hat Enterprise Linux, which feeds updates through a data center specific proxy server. The proxy's authoritative data is the Managed Red Hat Network server. This means that patching delays in Managed Red Hat Network server also delay updates in Managed Operations Service Level. For example, Red Hat Enterprise Linux v5.5 was delayed for several months after it was released by Red Hat.

| Distribution | Patching Mechanism  | Patching Servers | Frequency | Configuration |
| ------------ | ------------------- | ---------------- | --------- | ------------- |
| Ubuntu | unattended-upgrades | snet1-[dc].mirror.rackspace.com </br></br> snet2-[dc].mirror.rackspace.com Howbackup:archive.ubuntu.com, security.ubuntu.com | Nightly between 0000 and 0400 server time | /etc/apt/apt.conf.d/02periodic </br></br> /etc/apt/apt.conf.d/50unattended-upgrades |
| Red Hat Enterprise Linux | yum-cron | snet1-[dc].mirror.rackspace.com </br></br> snet2-[dc].mirror.rackspace.com (for epel and ius) proxy1.[dc].slicehost.com, proxy2.[dc].slicehost.com (Example: proxy1.dfw1, proxy2.ord1, etc) | Nightly between 0000 and 0400 server time | /etc/yum-cron </br></br> /etc/sysconfig/rhn/up2date |
| CentOS | yum-cron | snet1-[dc].mirror.rackspace.com </br></br> snet2-[dc].mirror.rackspace.com | Nightly between 0000 and 0400 server time | /etc/yum-cron |

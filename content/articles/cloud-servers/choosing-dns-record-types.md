---
node_id: 1503
title: Choosing DNS record types
type: article
created_date: '2012-07-24'
created_by: Rackspace Support
last_modified_date: '2016-01-15'
last_modified_by: Stephanie Fillmon
product: Cloud Servers
body_format: tinymce
---

<span> DNS uses different record types for different purposes. This
article helps you determine which record type you should use when
creating a DNS record in the Cloud Control Panel.</span>

**A/AAAA**

Use the A/AAAA name to point to an IP address. In simple cases, you may
have only a single A or AAAA record as your base record pointing to a
single IP address. However in most cases. you'll have serveral A or AAAA
records that point to different IP addresses.

**Note**: If you do have a base record (which is not actually required)
it must be an A or AAAA record. For example, you could have
www.mydomain.com as an A record that points to 1.2.3.4, and
www.domain.com might be a CNAME record that points
to www.myotherimportantdomain.com.  Likewise, you might have
a mail.domain.com record pointing to 5.6.7.8.

A is an IPv4 Address record.

AAAA is an IPv6 Address record. Use this record type only if your server
has an IPv6 address to point to.

**CNAME**

Use the Common Name (CNAME) record to point to another record.

**MX**

Use the Mail Exchange (MX) record for mail delivery. For
example, creating an MX record for domain.com would allow you to set up
an email address like <span
class="s2">mike@mydomain[.](mailto:mike@domain.com)com</span>.

**NS**

Use the Name Server (NS) record to delegate an authoritative DNS server
for a domain or subdomain.

**SRV**

Use the Server Locator record to designate a host and port for certain
services, such as LDAP,  for a domain.

**TXT**

Use the Text (TXT) record to store data types such as SPF or DKIM
records.

### Related Information

[Learn More About
DNS](/how-to/learn-more-about-dns)

### External Links

<http://en.wikipedia.org/wiki/List_of_DNS_record_types>

This Wikipedia page provides a listing of<span> </span>resource
records<span> stored in
the </span>zone[ ](http://en.wikipedia.org/wiki/Zone_file "Zone file")files<span> of
the </span>Domain Name System <span>(DNS).</span>


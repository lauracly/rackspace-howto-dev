---
node_id: 418
title: Preparing the Cloud Server to be a Mail Server
type: article
created_date: '2011-03-16'
created_by: Rackspace Support
last_modified_date: '2016-01-13'
last_modified_by: Nate Archer
product: Cloud Servers
body_format: tinymce
---

**Warning:** Email in the Cloud (Rackspace or otherwise), even with
today's vast standards, is considered to be "best effort" without any
guarantees for reliability or deliverability. Follow the steps below to
have a better email sending reputation. As an additional precaution, it
is helpful to research and consider using the following:

-   [DomainKeys Identified
    Mail (DKIM)](/how-to/rackspace-cloud-dns-additional-resources)
-   [Domain-based Message Authentication, Reporting &
    Conformance (DMARC) DNS records](http://www.dmarc.org/index.html)

It is vital that the Cloud Server has the basics such as the hostname
and Reverse DNS correctly set before we configure any sort of mail
service. This article looks at the hostname and reverse DNS (RDNS)
settings on the Cloud Server.

Contents
--------

-   [<span class="tocnumber">1</span> <span
    class="toctext">Assumptions</span>](#Assumptions)
-   [<span class="tocnumber">2</span> <span
    class="toctext">Hostname</span>](#Hostname)
-   [<span class="tocnumber">3</span> <span
    class="toctext">Reboot</span>](#Reboot)
-   [<span class="tocnumber">4</span> <span class="toctext">Reverse
    DNS</span>](#Reverse_DNS)
    -   [<span class="tocnumber">4.1</span> <span class="toctext">Change
        Reverse DNS in the Control
        Panel</span>](#Change_Reverse_DNS_in_the_Control_Panel)
    -   [<span class="tocnumber">4.2</span> <span class="toctext">Check
        the Reverse DNS</span>](#Check_the_Reverse_DNS)
-   [<span class="tocnumber">5</span> <span
    class="toctext">Summary</span>](#Summary)



<span class="mw-headline">Assumptions </span>
---------------------------------------------

The only assumptions made for these email articles are:

1: You are running and have set up Ubuntu Hardy (The instructions may
work on other distros but it has not been tested and is not guaranteed)



<span class="mw-headline">Hostname </span>
------------------------------------------

The first thing to look at is the Cloud Server hostname.

This is simply the 'name' of the Cloud Server and is used in the headers
of the email (the headers can be thought of as the address and sender
label on the email).

Setting the hostname via the command line involves the very simple
adjustment of a couple of files.

We can start by checking what the current hostname is:

    hostname -f

On my Cloud Server, the output is:

    cloudserver1

For these basic articles I am going to use the domain
'mail.democloud.com' - I am setting up a mail server so that makes
sense.

I need to change the hostname to match the domain:

    sudo nano /etc/hostname

Replace the current hostname (cloudserver1) with the one you need (in
this case mail.democloud.com).

The second file to edit is:

    sudo nano /etc/hosts

The default looks like this on my Cloudserver:

    127.0.0.1       localhost localhost.localdomain
    127.0.0.1       cloudserver1

Following on from what we are doing, replace 'cloudserver1' with
'mail.democloud.com'.

Of course, replace mail.democloud.com with your domain.



<span class="mw-headline">Reboot </span>
----------------------------------------

Conduct a quick reboot:

    sudo shutdown -r now

and check the hostname:

    hostname -f

The output is now:

    mail.democloud.com

Good start!



<span class="mw-headline">Reverse DNS </span>
---------------------------------------------

Now, we need to properly set the reverse DNS for the server.



### <span class="mw-headline">Change Reverse DNS in the Control Panel </span>

Navigate to your Server's DNS tab and scroll down to the Reverse DNS
section. Change the relevant field to the domain name which you'd like
in the rDNS record. (See [DNS - Creating a Reverse DNS
Record](/how-to/create-a-reverse-dns-record-0 "DNS - Creating a Reverse DNS Record"))



### <span class="mw-headline">Check the Reverse DNS </span>

The RDNS may take a while to propagate and you really need to wait until
it has done so before you can fully configure and test any mail setup.

To check the RDNS, you need to input the IP address if the Cloud Server
into the 'dig' command.

Note that 'dig' is not installed on a base Ubuntu Hardy Cloud Server:

    sudo aptitude install dnsutils

So, to check the RDNS:

    dig -x 208.75.84.20

In this case, the output includes the correct answer:

    dig -x 208.75.84.20
    ...
    ...
    ;; QUESTION SECTION:
    ;20.84.75.208.in-addr.arpa.     IN      PTR

    ;; ANSWER SECTION:
    20.84.75.208.in-addr.arpa. 3477 IN      PTR     mail.democloud.com.



<span class="mw-headline">Summary </span>
-----------------------------------------

Preparing the Cloud Server is a vital step in any mail setup - even if
'only' sending mail from your application to an administrator, it is
very important to get the basics right.


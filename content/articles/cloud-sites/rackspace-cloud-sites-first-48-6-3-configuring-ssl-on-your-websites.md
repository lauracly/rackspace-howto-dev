---
node_id: 127
title: 'Getting started with Cloud Sites: Configuring SSL on your websites'
type: article
created_date: '2011-03-14 20:26:42'
created_by: RackKCAdmin
last_modified_date: '2016-01-11 00:0206'
last_modified_by: renee.rendon
product: Cloud Sites
body_format: tinymce
---

**Note**: This article is written for our [Cloud Sites Control
Panel](https://manage.rackspacecloud.com/). You can get to it from the
Cloud Control Panel by clicking the Rackspace Cloud menu at the top of
the screen and selecting **Cloud Sites**.

### Previous section

[Getting Started with Cloud
Sites](https://www.rackspace.com/knowledge_center/getting-started/cloud-sites)

 

Secure Sockets Layer (SSL) is an encryption technology that protects
your visitors' private information while it's in transit via the
Internet.

When you ask your site's visitors to divulge personal and business
information, they need to trust you. They have to know that their data
is secure from eavesdropping, tampering, and even phishing attacks. And
the more they trust you, the more likely they are to complete forms,
purchase items, and share valuable information online. SSL certificates
let them know that they can confidently share their data with you.

Some applications that are configured to run SSL are web browsers like
Internet Explorer and FireFox; email programs like Outlook, Mozilla
Thunderbird, and Apple Mail.app; and SFTP (secure file transfer
protocol) programs. These programs are automatically able to receive SSL
connections.

Adding SSL to a website on Cloud Sites is a straightforward process.This
article provides the following information: 

-   [Supported types of SSL certificates](#supported_ssls)
-   [Generate a CSR for your site](#generateaCSR)
-   [Purchase a SSL certificate ](#ssl_purchase)
-   [Install the certificate](#ssl_install)
-   [SSL tips](#ssl_tips_and_tricks)

**Supported types of SSL Certificates**
---------------------------------------

The primary certificates supported on Cloud Sites are as follows:

-   Root Level certificates
-   Apache + OpenSSL

Cloud Sites allows installation of most chained certificates, including
Extended Validation (EV), multi-domain, and wild card
certificates. These will require installation to a primary Common Name
domain to work properly.

 

**Note**: Cloud Sites no longer supports *any* self-signed
certificates. 

**Generate a CSR for your site**
--------------------------------

Complete the following steps to generate a certificate signing request
(CSR), which you will need to have when you purchase an SSL certificate.

1.  Log in to the [Cloud Sites Control
    Panel](http://manage.rackspacecloud.com).
2.  Click **Hosting \> Cloud Sites**.
3.  Click the domain you want to add SSL to, and then click the
    **Security** tab.

    ![](http://c806394.r94.cf2.rackcdn.com/securitytab.png)

4.  In the **Permissions for Viewing Your Website** section, click
    **Install SSL Certificate**.

    ![](http://c806394.r94.cf2.rackcdn.com/installsslcertificatetab.png)

5.  Review the order summary and payment details, select the **Terms
    Agreement** check box, and teh click Finish. If you have questions
    about the charges, contact Support.

    ![](http://c806394.r94.cf2.rackcdn.com/ssltos.png)

6.  On the Install SSL Certificate page, click the **Start New
    Certificate** button.

7.  Complete the form and click the **Next Step** button when finished.

Your CSR is generated. With the CSR ready for use, you can proceed to
[purchasing a
certificate](https://admin.rackspace.com/knowledge_center/node/127/revisions/27345/view#ssl_purchase).

**Purchase a certificate**
--------------------------

SSL certificates are available from a number of third party sources.
Some recommended sellers are
[RapidSSL](http://www.rapidssl.com "http://www.rapidssl.com"),
[Geotrust](http://www.geotrust.com "http://www.geotrust.com"), and
[Verisign](http://www.verisign.com "http://www.verisign.com").

Follow the vendor's SSL certificate request process. In particular, the
vendor might require the following details:

-   Server type: Apache
-   SSL type: OpenSSL or modSSL
-   CSR: [You generated
    this](https://admin.rackspace.com/knowledge_center/node/127/revisions/27345/view#install_ssl)
    in the preceding section

After you have completed your certificate purchase, you're ready to
[install the
certificate](https://admin.rackspace.com/knowledge_center/node/127/revisions/27345/view#ssl_install).

**Install the certificate**
---------------------------

1.  Log in to the [Cloud Sites Control
    Panel](https://manage.rackspacecloud.com).
2.  Click **Hosting \> Cloud Sites**.
3.  Click the **domain** for which you generated the CSR for, and then
    click the **Security** tab. 
4.  In the **Permissions for Viewing Your Website** section, click
    **Enter Certificate File**.
5.  Enter the certificate information in the **Certificate** field.\
     \
     **Note**: Some vendors provide certificates in text format in an
    email or on their website, which makes copy and pasting the
    certificate easy. Other vendors may provide certificates as a
    **.crt** file. You can open this file in a plain text editor and
    retrieve the text for the certificate there.\
      
6.  If you have any SSL intermediate certificates, copy and paste them
    into the **Intermediate Certificate** field.
7.  Click **Next Step**.
8.  Confirm that the certificate details are correct and then click
    **Finish**.

**Note**: If you have any problems during the installation, contact
Support for assistance.

### **DNS update**

If Rackspace is managing your DNS, DNS for your site will be
automatically updated. It can take up to two hours for the new IP
addresses for your site to complete propagation. If you are managing
your own DNS, click the **Domain** tab to get your new IP addresses.

### **What to watch for**

Currently the Rackspace Cloud does not support wildcard
certificates--such as **\*.domain.com** or **\*.example.com**. These
certificates might or might not function as necessary. This feature is
currently under consideration.

Removing an SSL certificate from a site will change the site's IP
address in the same way that adding a new certificate changes the IP
address.  DNS must be updated in that case as well.

**SSL tips**
------------

-   [Force SSL on your PHP
    site](https://admin.rackspace.com/knowledge_center/index.php/How_do_I_force_SSL_on_my_PHP_site)
-   [Force SSL on your ASP/.NET
    site](https://admin.rackspace.com/knowledge_center/index.php/How_do_I_force_SSL_on_my_ASP.NET_site)

### Next section

[FTP/SSHFS/FTP
clients](http://www.rackspace.com/knowledge_center/article/getting-started-with-cloud-sites-ftpsshfsftp-clients)

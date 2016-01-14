---
node_id: 712
title: 'Rackspace Cloud Essentials: Tips and Tricks for .htaccess and web.config'
type: article
created_date: '2011-03-16 21:57:40'
created_by: RackKCAdmin
last_modified_date: '2016-01-04 15:1249'
last_modified_by: Nate.Archer
product: Cloud Sites
body_format: tinymce
---

**Note**: This article is written for our [Cloud Sites Control
Panel](https://manage.rackspacecloud.com/). You can get to it from the
Cloud Control Panel by clicking your name in the upper-right corner and
selecting [Cloud Sites Control
Panel](https://manage.rackspacecloud.com/).

### Previous section

[Getting Started with Cloud
Sites](https://www.rackspace.com/knowledge_center/getting-started/cloud-sites)

 

**In this article we're going to take a look at the .htaccess file**and
the**web.config file.** We'll discuss what they are, and how they're
used with Cloud Sites.

If you are using Windowa IIS, ASP/.NET then please click the
[web.config](#web_config) link to skip to the next portion of this
article.

If you are using Linux as your primary technology, then please continue
reading below.

-   [.htaccess](#htaccess)
-   [web.config](#web_config)

**What is .htaccess and what is it used for?**

[Wikipedia](http://en.wikipedia.org/wiki/Htaccess "http://en.wikipedia.org/wiki/Htaccess")
explains the **.htaccess** file as follows:

"In several web servers (most commonly Apache), .htaccess (hypertext
access) is the default name of a directory-level configuration file that
allows for decentralized management of web server configuration. The
.htaccess file is placed inside the web tree, and is able to override a
subset of the server's global configuration; the extent of this subset
is defined by the web server administrator. The original purpose of
.htaccess was to allow per-directory access control (e.g. requiring a
password to access the content), hence the name. Nowadays .htaccess can
override many other configuration settings, mostly related to content
control."

For more information, and several examples, the following links are
highly recommended:

-   [.htaccess-Guide.com](http://www.htaccess-guide.com/ "http://www.htaccess-guide.com/")
-   [JavascriptKit.com's "Comprehensive guide to
    .htaccess"](http://www.javascriptkit.com/howto/htaccess.shtml "http://www.javascriptkit.com/howto/htaccess.shtml")

For a more comprehensive technical overview, please see [the Apache
documentation on .htaccess
files](http://httpd.apache.org/docs/2.0/howto/htaccess.html "http://httpd.apache.org/docs/2.0/howto/htaccess.html").

On the Rackspace Cloud Sites platform, .htaccess can be used for
handling certain points of website security, PHP configuration changes,
as well as website operations. Below is an example of how an .htaccess
file is used for security.

-   [Deny certain IP addresses access to web
    site](http://www.rackspace.com/knowledge_center/index.php/How_do_I_deny_certain_IP_addresses_from_accessing_my_site "How do I deny certain IP addresses from accessing my site?")

**What is web.config and what is it used for?**

[Wikipedia](http://en.wikipedia.org/wiki/Htaccess "http://en.wikipedia.org/wiki/Htaccess") explains
the **web.config** file as follows:

Web.config is the main settings and configuration file for
an [ASP.NET](http://en.wikipedia.org/wiki/ASP.NET "ASP.NET") web
application. The file is an [XML
document](http://en.wikipedia.org/wiki/XML_document "XML document") that
defines configuration information regarding the web application. The
web.config file contains information that control module loading,
security configuration, [session
state](http://en.wikipedia.org/wiki/ASP.NET_state_management "ASP.NET state management") configuration,
and application language and compilation settings. Web.config files can
also contain application specific items such as database [connection
strings](http://en.wikipedia.org/wiki/Connection_string "Connection string").

For more information and several examples, the following links are
highly recommended:

-   [ASP.NET
    Configuration](http://msdn.microsoft.com/en-us/library/w7w4sb0w.aspx)
-   [Format of ASP.NET Configuration
    Files](http://msdn2.microsoft.com/en-us/library/ackhksh7(VS.71).aspx)

Below are some of the most commonly used functions for the web.config
file:

1.  [How do I add impersonation to my ASP/.NET Cloud
    Site](http://www.rackspace.com/knowledge_center/index.php/How_do_I_add_impersonation_to_my_ASP.NET_site)
2.  [How do I enable detailed errors in Classic ASP and server side
    errors in Cloud
    Sites](http://www.rackspace.com/knowledge_center/index.php/How_do_I_enable_detailed_errors_in_classic_ASP)
3.  [How do I setup customErrors in ASP/.NET on Cloud
    Sites](http://www.rackspace.com/knowledge_center/index.php/How_do_I_enable_detailed_errors_in_ASP.NET)
4.  [How to rebuild an ASP/.NET application in Cloud
    Sites](http://www.rackspace.com/knowledge_center/index.php/How_to_Rebuild_the_Application_in_Cloud_Sites)
5.  [How do I bin deploy an ASP/.NET application on Cloud
    Sites](http://www.rackspace.com/knowledge_center/index.php/How_do_I_bin_deploy_an_ASP/NET_assembly)
6.  [Why are my HttpHandlers not working for my ASP/.NET site on Cloud
    Sites](https://www.rackspace.com/knowledge_center/article/httphandlers-not-working-in-integrated-mode-for-aspnet-sites-on-cloud-sites)
7.  [How do I rectify an invalid view state error with an ASP/.NET
    application](http://www.rackspace.com/knowledge_center/index.php/How_do_I_rectify_an_invalid_view_state_error_with_an_ASP.NET_application)
8.  [ASP/.NET Integrated
    Mode](http://www.rackspace.com/knowledge_center/article/aspnet-integrated-mode-on-cloud-sites)
9.  [Overview of Cloud Sites modified Medium
    Trust](http://www.rackspace.com/knowledge_center/index.php/Overview_of_modified_Medium_Trust)

### Next section

[Configuring SSL on your
website(s)](http://www.rackspace.com/knowledge_center/article/getting-started-with-cloud-sites-configuring-ssl-on-your-websites)

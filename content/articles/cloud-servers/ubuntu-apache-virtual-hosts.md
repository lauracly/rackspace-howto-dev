---
node_id: 108
title: Set up Apache virtual hosts on Ubuntu
type: article
created_date: '2011-03-09 19:54:25'
created_by: RackKCAdmin
last_modified_date: '2015-12-29 17:0916'
last_modified_by: stephanie.fillmon
product: Cloud Servers
body_format: tinymce
---

undefined&mdash; Apache will apply named based virtual host logic and settings
for HTTP requests made on any available interface (\*) at port 80.

**Note**: The placement of the default NameVirtualHost directive in
'ports.conf' is new to Ubuntu's Apache layout; prior Ubuntu releases
placed a similar setting in the default vhost.

### Define custom virtual hosts

Now you are ready to add your own virtual hosts so that you can start to
serve your domains.

Create the vhost file for domain1:

    sudo nano /etc/apache2/sites-available/domain1.com.conf

The contents looks as follows:

    # Place any notes or comments you have here
    # It will make any customisation easier to understand in the weeks to come

    # domain: domain1.com
    # public: /home/demo/public_html/domain1.com/

    <VirtualHost *:80>

      # Admin email, Server Name (domain name) and any aliases
      ServerAdmin webmaster@domain1.com
      ServerName  domain1.com
      ServerAlias www.domain1.com


      # Index file and Document Root (where the public files are located)
      DirectoryIndex index.html
      DocumentRoot /home/demo/public_html/domain1.com/public


      # Custom log file locations
      LogLevel warn
      ErrorLog /var/log/apache2/error-mydomainname.com.log
      CustomLog /var/log/apache2/access-mydomainname.com.log combined

 

Enable the site
---------------

Enable the site as follows:

    sudo a2ensite domain1.com

 

 

The output of the command is as follows:

    Site domain1.com installed; run /etc/init.d/apache2 reload to enable.

 

Run the recommended command:

    sudo /etc/init.d/apache2 reload

 

Navigate to the site
--------------------

To test the domain without creating a DNS zone and records on some
Internet name servers, you can modify the '/etc/hosts' file on your
local computer to include some entries mapping 'domain1.com',
'domain2.com', and the rest to the demo Cloud Server's public IP
address:

    127.0.0.1    localhost
    ...

    # entries related to the demo Cloud Server
    123.45.67.890   domain1.com
    123.45.67.890   www.domain1.com
    123.45.67.890   domain2.com
    ...

 

 

The location of the 'hosts' file varies depending on what OS is loaded
on your local computer.

**Note**: Entries in the 'hosts' file must be removed prior to testing
and using live DNS zones and records created on Internet name servers.
Failure to remove them might lead to confusion on your part and
inaccurate tests of new or modified public DNS records.

With such changes made for testing purposes, you can navigate to your
site in a web browser on your local computer:

![apache-vhostworking-domain1.jpg](http://articles.slicehost.com/assets/2008/12/5/apache-vhostworking-domain1.jpg)

 

 

The contents of public/index.html file is shown.

Use the ServerAlias
-------------------

Note that in the vhost file, you set a ServerAlias. If you have the DNS
set up correctly, you can also use that address:

![apache-vhostworking-wwwdomain1.jpg](http://articles.slicehost.com/assets/2008/12/5/apache-vhostworking-wwwdomain1.jpg)

 

We'll talk about forcing one address or the other in a later article
about rewrite rules.

Repeat the process for the other domain
---------------------------------------

To create and enable domain2.com, repeat the process as follows:

1.  Create the vhost file:

        sudo nano /etc/apache2/sites-available/domain2.com
        ...
        # Enter the details for domain2.com as per the example shown above

2.  Enable the site and restart Apache:

        sudo a2ensite domain2.com
        ...
        sudo /etc/init.d/apache2 reload

3.  Navigate to the second domain:

        http://domain2.com
        or
        http://www.domain2.com

You should see the 'domain2.com' index file.

View log files
--------------

As defined in the vhosts file, each domain has its own log files.

List the logs for your domains:

    ls /var/log/apache2/error-mydomainname.com.log

 

The output is exactly as expected:

    access.log  error.log

 

Default vhost file
------------------

Although you changed the default virtual host, you did leave it in
place.

If someone enters the IP address of the cloud server, they are served
the contents of that default vhosts file (if you did not set up a
separate vhost for the IP address).

Why are they served from that vhost file?

Apache searches the enabled vhost files in alphabetical order and if it
can't find one for the requested IP address or domain name, it serves
the first one (alphabetically).

If you had disabled or deleted the default vhost file, then the contents
of domain1.com would be displayed (being before domain2.com
alphabetically).

This is something to consider when planning your websites. Do you want a
particular domain to be the default? Do you want the IP address to have
completely different content?

Set the admin email address
---------------------------

Set the email address for the server administrator. This address is used
if you set up the server to contact you when errors occur. It is also
shown in the ServerSignature if its value is set to Email. (See the
section, [Define Apache footers](#Apache_Footers).)

    ServerAdmin webmaster@domain.com

 

 

Set the domain name
-------------------

Set the domain name (ServerName) for the virtual host. You can have as
many aliases (ServerAlias) as required. For example, you can have
domain.com and domain.net point to the same content.

    ServerName domain.com
    ServerAlias www.domain.com

 

**Note**: This is not a rewrite rule, but the the domains defined here
will serve the same content (assuming you have set the DNS to point to
your Cloud Server IP).

Define the index file
---------------------

Define the index file (the home page that is shown when the domain
address is entered). This is useful if you have want the user to be
directed to an alternate page or to a nonstandard home page.

    DirectoryIndex index.html

 

**Note**: This is not a good method for redirecting users because they
might go directly to a nonspecified page, such as domain.com/index.php,
while the DirectoryIndex value works only for those entering domain.com.

Define the documents path
-------------------------

Define the location of the domain's public files. Use an absolute path
name.

    DocumentRoot /home/demo/public_html/domain.com/public

 

 

Set the log files
-----------------

Set the log levels and the location for the virtual hosts' log files.

    LogLevel warn
    ErrorLog  /var/log/apache2/error-mydomainname.com.log
    CustomLog /var/log/apache2/access-mydomainname.com.log combined

 

 

Define error documents
----------------------

Set the ErrorDocument, which is used for all the standard error
messages.

    ErrorDocument 404 /errors/404.html
    ErrorDocument 403 /errors/403.html

 

 

In this example, there is an 'errors' folder in the public directory.
Each error document was created and placed in the errors folder. The
paths shown are relative to the DocumentRoot folder defined previously.

If error messages are not defined, Apache generates its own error pages.
Custom error pages are more user friendly and can be customized as much,
or as little, as you want.

Define Apache footers
---------------------

Define ServerSignature to specify whether the server details are
displayed in any server-generated error pages or index lists. Options
are On, Off, and Email.

    ServerSignature On

 

 

The level of detail in the signature is configured via ServerTokens,
which cannot be set in the Virtual Hosts file. For Ubuntu's Apache
layout, this is properly set in '/etc/apache2/conf.d/security'. See the
Apache configuration \#2 NEED LINK article for more details.

If ServerSignature is set to **Email**, the ServerAdmin email will be
displayed.

Enable cgi-bin
--------------

Enable the cgi-bin location as defined by the custom virtual hosts
layout. You can leave cgi-bin in the DocumentRoot location if you so
want.

    ScriptAlias /cgi-bin/ /home/demo/public_html/domain.com/cgi-bin/
    <Location /cgi-bin>
      Options +ExecCGI
    </Location>

 

 

Set directory options
---------------------

Set the options for the specified directory. The following example
enables the FollowSymLinks option for the public directory of
domain.com.

      Options FollowSymLinks

 

 

Following are other options that you can set:

### Directory browsing option

To turn off directory browsing, use -Indexes. To turn on directory
browsing, use +Indexes.

    Options -Indexes

 

 

### SSI option

Enable or disable Server Side Includes. The following example disables
it.

    Options -Includes

 

 

### Symlinks option

Enable or disable the option to follow symlinks. Be careful with this
option because it can lead to security risks (inadvertently linking to
configuration folders).

    Options -FollowSymLinks

 

 

You can consider using the SymLinksIfOwnerMatch directive instead of
FollowSymLinks. The SymLinksIfOwnerMatch directive allows symbolic links
to be followed only if the owner of the link is identical to the owner
of the target file or directory (in terms of Linux filesystem
ownership/permissions). This prevents many of the security risks that a
simple FollowSymlinks directive can create.

### .htaccess option

Set AllowOverride to None to disable .htaccess support. Set it to All to
allow support.

    AllowOverride None

 

 

You can also specify which .htaccess features to enable, such as:

    AllowOverride AuthConfig Indexes

 

 

The Apache
[htaccess](http://httpd.apache.org/docs/2.2/howto/htaccess.html "http://httpd.apache.org/docs/2.2/howto/htaccess.html")
and
[AllowOverride](http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride "http://httpd.apache.org/docs/2.2/mod/core.html#allowoverride")
docs have more information about the different features.

Remember to specifically protect your .htaccess file. You can do this by
renaming it to something obscure and denying access access to the file
from external sources:

    AccessFileName .myobscurefilename
    <Files ~ "^\.my">
        <SatisfyAll>
        Require all denied
        </SatisfyAll>
    </Files>

 

**Note**: The preceding example is formatted for Apache 2.4. If using
2.2, replace **\<SatisfyAll\> Require all denied  \</SatisfyAll\> **
with**Order Allow,Deny | Deny from all | Satisfy all**.

### No Options

Specify None to turn off all the available options.

    Options None

 

 

### Options hierarchy

The options directives can be set per directory, as shown in the
following example:

      AllowOverride None
      Options None
      
    AllowOverride All

 

 

The first directory setting would turn off all options and disable
.htaccess support for all directories.

However, the second directory setting would override the first and allow
.htaccess support for the domain.com/public directory.

Summary
-------

The virtual hosts file is an easy tool to use but a very powerful one.
We recommend that you enter one setting and then test it. Then enter the
next setting and test, and so on.

After you become familiar with it, you will see you have fine control
over all of your web folders and files.

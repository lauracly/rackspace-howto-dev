---
node_id: 89
title: PHP Sessions State Servers on Cloud Sites And How To Fix Non Working PHP Sessions
type: article
created_date: '2011-03-09'
created_by: Rackspace Support
last_modified_date: '2015-12-29'
last_modified_by: Stephanie Fillmon
product: Cloud Sites
body_format: tinymce
---

Session state servers are being implemented for PHP applications. This
will improve the performance of most sites by setting the default
session handler to the state servers. Session data will be accessible
from all PHP web nodes from a purpose built server pool instead of the
local or network file system. This avoids common problems with
performance, garbage collection, and sessions not following users to
other servers.

Special care has been taken to ensure functionality is compatible with
the default 'files' handler. Session save paths are still honored to
emulate sharing of a file system directory. If you set the same save
path between multiple sites on a single account it has the same effect
as using a shared file system folder. If for some reason the session
handler does not work, the original behavior can be restored in
.htaccess with the following:

    php_value session.save_handler files



If you are experiencing a problem with the standard way sessions are
stored, you can change how your PHP sessions are handled by using a
.htaccess file. If your application currently explicitly sets the use of
the 'files' handler, we suggest disabling it  or explicitly setting it
to 'redisr' to benefit from the performance of the state servers.



<span class="mw-headline">How do I make the changes?</span>
-----------------------------------------------------------

You can change how your PHP sessions are handled by using a .htaccess
file containing the following directives:

    php_value session.save_path /mnt/stor1-wc1-dfw1/123456/www.domain.com/web/sessions
    php_value session.save_handler files

This changes the life time of the session and sets your application to
save the session in a place of your choosing.

You will want to change the path of the last line in the example above
to use your website's absolute path. [Please see this
article](/how-to/locate-the-linux-path-for-your-cloud-sites-website "How do I find my website's Linux path?")
to locate your website's absolute path.

Your website's absolute path should resemble this:
**/mnt/stor1-wc1-dfw1/123456/www.domain.com/web/content**



<span class="mw-headline">Where should I store my sessions?</span>
------------------------------------------------------------------

We recommend storing your sessions in a directory above the
public-facing **content** directory, such as the **web** directory. The
recommended practice is to login to your FTP and create a **sessions**
directory within your **web** directory. At this point your session save
path should be:
**/mnt/stor1-wc1-dfw1/123456/www.domain.com/web/sessions**

So the last line in your .htaccess file would resemble the following:

    php_value session.save_path /mnt/stor1-wc1-dfw1/123456/www.domain.com/web/sessions




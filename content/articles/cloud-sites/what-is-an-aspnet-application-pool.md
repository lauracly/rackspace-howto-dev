---
node_id: 722
title: What Is An ASP.NET Application Pool?
type: article
created_date: '2011-03-16 21:57:40'
created_by: RackKCAdmin
last_modified_date: '2011-09-07 17:0306'
last_modified_by: matt.wheeler
product: Cloud Sites
body_format: tinymce
---

An application pool is a form of encapsulation to prevent the effects of
bad code being executing from impacting other processes. Each
application pool has its own worker process associated with it. By
default, each site's /content directory is an application pool. In some
situations, you may have installed a separate application into a
sub-directory, such as /content/gallery. In this case, you may need to
have the /gallery sub-directory turned into an application pool. By
contacting support, this can be processed for you.

For in-depth information concerning application pools, please see the
following article:

[http://www.developer.com/net/asp/article.php/2245511](http://www.developer.com/net/asp/article.php/2245511 "http://www.developer.com/net/asp/article.php/2245511")

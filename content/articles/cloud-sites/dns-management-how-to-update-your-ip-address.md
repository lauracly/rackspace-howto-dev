---
node_id: 1216
title: 'DNS management: How to update your IP address'
type: article
created_date: '2011-09-27'
created_by: Rackspace Support
last_modified_date: '2014-11-12'
last_modified_by: David Hendler
product: Cloud Sites
body_format: markdown_w_tinymce
---

One of the greatest conveniences of Rackspace Cloud Sites is automatic DNS provisioning when you add a new domain through your Control Panel. But what if you're hosting your DNS externally to Rackspace? How will you update your DNS records to make your website accessible?

The following sections show you how to locate your Rackspace Cloud Sites DNS entries so that you can add them to your external DNS provider. This will ensure your DNS is pointing accurately to your Cloud Site.

## Using the Cloud Sites Control Panel

1.  Log in to the [**Cloud Sites Control Panel**](https://manage.rackspacecloud.com/pages/Login.jsp). You use the control panel to find your DNS entries.

2.  Click on **Hosting > Cloud Sites**.

     <img alt="" src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/sitessidebar.png" style="width: 138px; height: 172px;" />

3.  Select the domain name for which you want to obtain DNS information.

4.  Click on the **DNS** tab toward the top of your screen.

     <img alt="" src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/sitesdnsbar.png" style="width: 476px; height: 25px;" />

5.  Scroll down to the **DNS Management** section within the DNS tab. This area shows all of the DNS entries for. The two entries that you need are the www.domain.com, and the root domain.com as indicated in the following screenshot.

     <img alt="" height="150" src="http://c766433.r33.cf2.rackcdn.com/arecords.png" />

6. Replicate these DNS entries to your external DNS provider. The process will differ depending on the service. In the preceding screen shot, you can see **A** and **CNAME**" entries in the **Type** column. Ensure that you at least replicate the **A** entries for the root domain and **www**, although you might also want to set the **ftp** record (the address used to transfer files to the domain). If you are using email through Cloud Sites, you should also set up the **CNAME** entries for **mail** and **webmail**.

## Using the Cloud Control Panel

You can also edit and update your DNS records through the DNS page of the Cloud Control Panel.

**NOTE:** It can take a while for the DNS setting changes to propagate to the rest of the Internet, so your domain might not point to your Cloud Site right away. You can bypass DNS and verify that your site is up by using the **Testing URL** listed in the site's **General Settings** tab. If you still can't access the site through your domain name after an hour or two, contact your DNS provider for assistance.

1.  Log in to the [Cloud Control Panel](https://mycloud.rackspace.com).

     <img alt="" src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/1216-4.png" style="width: 452px; height: 288px; border-width: 2px; border-style: solid;" />

2.  Select **DNS** from the menu at the top of the page.

     <img alt="" src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/1216-1.png" style="width: 818px; height: 53px; border-width: 2px; border-style: solid;" />

3.  Click on the domain name for which you want to obtain the DNS information.

     <img alt="" src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/1216-2_0.png" style="width: 785px; height: 154px; border-width: 2px; border-style: solid;" />

4.  On the **Domain Details** page, the DNS entries are located under the **Records** heading. The two entries that you need are the www.example-domain.com and the root example-domain.com, as indicated in the following screenshot.

     <img alt="" src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/1216-3.png" style="width: 639px; height: 188px; border-width: 2px; border-style: solid;" />

5.  Replicate these DNS entries to your external DNS provider. The process will differ depending on the service. In the DNS records list, you can see **A** and **CNAME**" entries in the **Type** column. Ensure that you at least replicate the **A** entries for the root domain and **www**, although you might also want to set the **ftp** record (the address used to transfer files to the domain).

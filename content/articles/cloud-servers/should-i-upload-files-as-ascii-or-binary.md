---
node_id: 131
title: Should I upload files as ASCII or binary?
type: article
created_date: '2011-03-15'
created_by: Rackspace Support
last_modified_date: '2015-05-06'
last_modified_by: Kelly Holcomb
product: Cloud Servers
body_format: tinymce
---

Deciding on how you should upload a file depends strictly on the type of
file you are uploading. Files such as HTML, ASP, PHP, CGI, and PL
documents should be uploaded in ASCII mode.

A general rule for knowing how a file should be uploaded is: anything
that you can view with a text editor should be transferred in ASCII
mode. Binary files, such as GIF or JPEG images, ZIP files, and
executables should be transferred in BINARY mode.

The majority of FTP programs have an AUTO mode which switches
dynamically between ASCII or BINARY upload modes depending on the type
of file you are uploading. If you plan on using the AUTO feature, make
sure you check the program&rsquo;s list of ASCII file extensions; any file not
included in the program&rsquo;s list of ASCII extensions will be uploaded in
BINARY.




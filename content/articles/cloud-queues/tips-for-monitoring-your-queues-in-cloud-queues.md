---
node_id: 3658
title: Tips for Monitoring Your Queues in Cloud Queues
type: article
created_date: '2013-08-21'
created_by: Megan Meza
last_modified_date: '2016-01-11'
last_modified_by: Rose Contreras
product: Cloud Queues
body_format: markdown_w_tinymce
---

**Note:** Be sure to set up your [authentication token](/how-to/cloud-queues-curl-cookbook) before completing the terminal steps for creating your cloud queue.</p>

The steps in this process will return queue statistics, including the number of messages that exist in the queue. These are broken out by status.

## Monitoring through the API

Send the following request.

### Queue status template

       GET /v1/queues/{queue_name}/stats

### Request

Substitute your cloud queue information for the sample information:

       GET /v1/queues/fizbit/stats HTTP/1.1
       Host: marconi.example.com

Your cloud queue statistics are returned:

### Response

       HTTP:/1.1 200 OK
       {
         "messages": {
           "free": 146929,
           "claimed": 2409,
           "total": 149338,
           "oldest": {
               "href": "/v1/queues/fizbit/messages/50b68a50d6f5b8c8a7c62b01",
               "age": 63,
               "created": "2013-08-12T20:44:55Z"
           },
           "newest": {
               "href": "/v1/queues/fizbit/messages/50b68a50d6f5b8c8a7c62b01",
               "age": 12,
               "created": "2013-08-12T20:45:46Z"
           }
       }

## Monitoring through the Cloud Control Panel

You can view your cloud queue statistics in the Cloud Control Panel.

1. Log in to the Cloud Control Panel.

2. In the top navigation bar, click Servers > Message Queueing.

     <img src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/1560-3658-newimg.png" width="483" height="247" border="1" alt=""  />

3. Click on your queue name to go to the Queue Details page.

      <img src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/3658-tipsformonitoring-2_0.png" width="793" height="590" border="1" alt=""  />

**Note:** If total is 0, then the "oldest" and "newest" message statistics are not included.

You can find more developer information in the [Getting Started Guide](http://docs.rackspace.com/queues/api/v1.0/cq-gettingstarted/content/DB_Overview.html) and [API Developer Guide for Cloud Queues](http://docs.rackspace.com/queues/api/v1.0/cq-devguide/content/overview.html).

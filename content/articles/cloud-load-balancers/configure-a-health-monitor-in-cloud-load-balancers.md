---
node_id: 1492
title: Configure a health monitor in Cloud Load Balancers
type: article
created_date: '2012-07-24'
created_by: Rackspace Support
last_modified_date: '2016-01-11'
last_modified_by: Stephanie Fillmon
product: Cloud Load Balancers
body_format: tinymce
---

What is a health monitor?
-------------------------

The Cloud Load Balancers service includes a health monitoring operation
that periodically checks the health of the nodes associated with your
load balancer to ensure that they are responding correctly. You
can enable one health monitor per load balancer.

Why is a health monitor important?
----------------------------------

If the health monitor determines that a node is not responding, the node
is removed from the load balancer's rotation until the health monitor
determines that the node is functional. The health monitor periodically
performs health checks of each node, including new nodes that are added
to the load balancer. By performing these health checks, the health
monitor helps keep your load balancer operating smoothly by routing
traffic only to nodes that are functioning properly.

### To configure a health monitor

1.  Log in to the Cloud Control Panel.
2.  In the top navigation bar, click **Networking &gt; Load
    Balancers.** All existing load balancers for your account
    are displayed.
3.  Click the gear icon next to the name of the load balancer for which
    you want to create a health monitor, and select **Edit Health
    Monitoring**.
    <img src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/1492-confighealthmon-2_0.png" width="212" height="380" />
4.  In the popup dialog box, select a **Monitor Type:**

    -   **CONNECT**: The Connect health monitor connects to each node on
        its defined port to ensure that the service is
        listening correctly. The Connect monitor is the most basic type
        of health check and does no postprocessing or protocol-specific
        health checks. Provide the required information for this
        monitor.

        <img src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/1492-confighealthmon-3.png" width="354" height="338" />

        -   **Interval**: Minimum number of seconds to wait before
            executing the health monitor; must be a number between 1
            and 3600.
        -   **Timeout**: Maximum number of seconds to wait for a
            connection to be established before timing out; must be a
            number between 1 and 300.
        -   **Attempts**: Number of permissible monitor failures before
            removing a node from rotation; must be a number between 1
            and 10.
    -   **HTTP**: The HTTP health monitor is more intelligent than the
        Connect monitor. It can process an HTTP response to determine
        the actual condition of a node. Provide the required information
        for this monitor.

        <img src="https://8026b2e3760e2433679c-fffceaebb8c6ee053c935e8915a3fbe7.ssl.cf2.rackcdn.com/field/image/1492-confighealthmon-4.png" width="323" height="378" />

        -   **Interval**: Minimum number of seconds to wait before
            executing the health monitor; must be a number between 1
            and 3600.
        -   **Timeout**: Maximum number of seconds to wait for a
            connection to be established before timing out; must be a
            number between 1 and 300.
        -   **Attempts**: Number of permissible monitor failures before
            removing a node from rotation; must be a number between 1
            and 10.
        -   **HTTP Path**: The HTTP path that will be used in the
            sample request.
        -   **Status Regex**: A regular expression that will be used to
            evaluate the HTTP status code returned in the response. For
            example, you could use the regular expression
            **\^(500|40\[1348\])\$** to look for *unsuccessful* status
            codes (500, 401, 403, 404, and 408) returned in the
            response, or you could use the regular expression
            **\^\[2\]\[0\]\[02\]\$** to look for *successful* status
            codes of 200 and 202 in the response.
        -   **Body Regex**: A regular expression that will be used to
            evaluate the contents of the body of the response. For
            example you could use the regular expression
            **\^.\*(Unauthorized|Forbidden|Not Found|Timeout|Server
            Error).\*\$** to look for any of those potentially
            problematic strings in the body of the response, or you
            could use the regular expression **\^success\$** to look for
            the string **success**.

    **Note**: The system evaluates only the first 2048 bytes of the
    response against the body regex that you specify, so you should test
    accordingly.

    **Tip**: To debug the HTTP health monitoring, you should test the
    body regex against the IP address of the nodes that are being
    disabled.  You can use the following cURL command to see what the
    health monitoring analyzes:

        curl -s -r 0-2048 https://YOUR_IP_ADDRESS | head -c 2048 | egrep "YOUR_REGULAR_EXPRESSION"

5.  Click **Save Monitoring Settings**


You have now configured a health monitor for your load balancer. To
disable the health monitor, follow steps 1 through 3, and then
click **Disable **in the pop up dialog box. In the confirmation dialog
box, click **Disable Health Monitor**.






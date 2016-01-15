---
node_id: 4763
title: Using the MyRackspace Firewall Manager
type: article
created_date: '2015-07-28 14:53:02'
created_by: rose.contreras
last_modified_date: '2016-01-13 20:2846'
last_modified_by: rose.contreras
product: Cloud Servers
body_format: markdown_w_tinymce
---

<a name="top"> </a>

The MyRackspace Firewall Manager application is an upgraded version of the firewall control panel, which enables you to view and edit your firewall configurations. The Firewall Manager is available for all Cisco PIX, Cisco ASA, and Juniper SRX 100/240 firewalls. It is not available for Cisco PIX 515/525/535 URFO and firewalls in a high-availability configuration.

The Firewall Manager allows you to perform the following actions on the firewall’s inbound access control list:

- Add permit policies
- Add and delete IP addresses to be denied by means of a blacklist
- Add and delete IP addresses from address sets prefixed with <code>fwcp-</code>
- Delete single deny policies
- Add comments (notes) to a permit policy, deny policy, IP addresses in the blacklist, and IP addresses in an address set
prefixed with <code>fwcp-</code>
- View and export (.csv) changes that occurred on the firewall
- Export (.csv) the firewall’s inbound access list


###  Contents

  1. [Firewall user agreement](#fua)
  2. [Firewall Manager overview](#fmo)
  3. [Add a permit policy](#app)
  4. [Copy a policy](#cop)
  5. [Delete a policy](#dap)
  6. [Add a comment to a permit or deny policy](#acpd)
  7. [View and manage IP groups](#vma)
  8. [Manage the blacklist](#mbl)
  9. [View the Change Log](#vcl)
  10. [View static NATs (network address translations)](#nat)

<a name="fua"> </a>

## Firewall user agreement

Every three months, users with administrative and editing privileges are prompted to accept the Firewall User Agreement terms for each firewall. After you accept the user agreement, you and the primary contact person on the account receive a confirmation email. If you choose not to accept the agreement, you can still view your firewall configuration, but you cannot modify it.

<img src="/knowledge_center/sites/default/files/field/image/926-1.1.png" width="482" height="38" alt="" border="1"  />

[back to top](#top)

<a name="fmo"> </a>

## Firewall Manager overview

This section describes the main concepts about and attributes that you define for policies in the Firewall Manager.

### Hit Count

For Cisco PIX and ASA firewalls, access list hit counts are used to determine policy usage. Any policy that has a hit count of zero is considered as unused. You can view the access list hit counts in the **Hit Count** column. Hit counts are not enabled by default on the Juniper SRX 100 or 240 firewall. You can enable the hit count on a per-policy basis. However, if you enable it, the hit counts are not visible in the Firewall Manager. The access list hit counts are reset whenever the firewall is restarted. We plan to add support for this feature in a future version.

### Access control list

An <em>access control list</em> is a list of policies that the firewall evaluates when governing traffoc for a certain traffic path. With the Firewall Manager, you can manage only the firewall’s inbound traffic.

### Protocol

You can choose an IP (all ports), TCP (single port), or UDP (single port) protocol when you create a policy.


  - **IP (all ports):** Creates an IP policy that makes all ports and services on your server available from the IP address or address range that you supply. This protocol gives the supplied IP address or range of addresses complete access through the firewall. If you select this protocol, you  cannot specify a port number.<br />
  <a name="warning">**Best practices warning:** Do not use an IP address unless it is absolutely necessary. More traffic results in less security.</a><br /><br />
  - **TCP (single port):** You must pair this protocol with select ports. This is the most commonly used port. If you are unsure of which port to use, choose this one.<br /><br />
  - **UDP (single port):** You must pair this protocol with select ports.


For more information about TCP and UDP protocols, see the <a href="#destport">Destination port</a> section of this article</a>.

**Note:** The Protocol field sometimes states undefined. This behavior is expected for Juniper firewalls. The protocol is defined on the firewall itself and is not included in the output from the firewall. We are investigating how to display the protocol in a future version of the Firewall Manager.

<a name="source"> </a>

### Source IP address

The source IP address is the same as the IP address of the visiting client. It is the IP address that you want to allow through the firewall for a given destination port or service.

The source IP is often set to **Any IP** for web and similar services. For services such as FTP and email access, the source IP is often limited to just a few client IP addresses. See the <a href="#warning">best practices warning</a> in the previous section. You can choose the following options:


  - **Enter IP:** Allows you to enter a specific IP address
  - **Any IP:** Allows traffic from any source IP address through the firewall
  - **Get My Current IP:** Automatically retrieves your client’s IP address


### Netmask source and destination

Netmasks are a way to specify a range of IP addresses. If you enter an IP address in the **Source** or **Destination** fields, you can select a netmask. The default option is <code>**/32 (255.255.255.255)**</code>. Netmasks are listed in both Classless Inter-Domain Routing (CIDR) notation (also known as slash notation) and IP format. Following is a list of allowed IP address ranges:

CIDR | Netmask | Number of hosts in each range |
--- | --- | ---
/24 | 255.255.255.0 | 256 (0-255)
/25 | 255.255.255.128 | 128 (0-127 or 128-255)
/26 | 255.255.255.192 | 64 (0-63, or 64-127, or 128-192, or 192-255)
/27 | 255.255.255.224 | 32 (0-31, 32-63, 64-95, others, 192-233, 224-255)
/28 | 255.255.255.240 | 16 (0-15, others, 240-255)
/29 | 255.255.255.248 | 8 (0-7, others, 248-255)
/30 | 255.255.255.252 | 4 (0-3, others, 252-255)
/32 | 255.255.255.255 | 1 (single IP address)

### Destination IP address

 The destination IP address is the target IP address that resides on the server behind the firewall. See <a href="source">Source IP</a> address for the available options. You can enter an IP address, select **Any IP**, or select an IP address from the menu that includes the primary and secondary IP addresses of the devices behind the firewall.

**Note:** The new **Search by Device Name** feature is now available in the Firewall Manager.

<a name="destport"> </a>
### Destination port

If you select either the TCP or UDP protocol, you can enter a port number or select one from the menu of common ports. Ports 1 to 65535 are accepted.

The following port and protocol combinations are <em>not</em> permitted:


  - Port 21 and UDP
  - Port 22 and UDP
  - Port 25 and UDP
  - Port 69 and TCP
  - Port 80 and UDP
  - Port 110 and UDP
  - Port 115 and UDP
  - Port 443 and UDP


### Cisco PIX and ASA firewalls

For Cisco PIX and ASA firewalls, access list hit counts are used to determine policy usage. Any policy that has a hit count of zero is considered as unused. You can view the access list hit counts in the **Hit Count** column. Hit counts are not enabled by default on the Juniper SRX 100 or 240 firewall. You can enable the hit count on a per-policy basis. However, if you enable it, the hit counts are not visible in the Firewall Manager. The access list hit counts are reset whenever the firewall is restarted. We plan to add support for this feature in a future version.

[back to top](#top)

<a name="app"> </a>

## Add a permit policy

You can open a single port to all server IP addresses for a specific IP address. **Note:** Do not perform this action unless the source IP address is trusted; otherwise, any device provisioned in the future will be accessible by this source.

In the following image, a policy was added to allow an alternate SMTP (Port 587) mail traffic through the firewall from the IP address 207.250.49.146.

**Note:**

<img src="/knowledge_center/sites/default/files/field/image/926-4763-1_0.png" width="550" height="236" border="2" alt=""  />

The following image shows a protocol that was changed to IP (all ports). When you select this protocol, you cannot enter or select a port number.

<img src="/knowledge_center/sites/default/files/field/image/926-476-2.png" width="552" height="236" border="1" alt=""  />

[back to top](#top)
<br />

<a name="cop"> </a>

## Copy a policy

Click **copy** to copy an existing policy. The form fields are automatically populated where possible. You can then modify the policy before adding it. You cannot copy the following kinds of policies:

  1. Single deny policies
  2. Policies that reference an address set
  3. Locked policies

The **copy** icon is not displayed for these kinds of policies on the Firewall Manager screen.

[back to top](#top)

<a name="dap"> </a>

## Delete a policy

With the File Manager, you can delete permit policies and single deny policies by using the following steps:


  - In the Firewall Manager, select the check box for the policy that you want to delete.<br /><br />
  - Click **Delete Selected Policies** on the side bar.<br /><br />

If you want to delete multiple policies, you must delete them one at a time. Some policies do not display a check box and cannot be deleted. These policies allow Rackspace support technicians and specific systems to access your server.

[back to top](#top)

<a name="acpd"> </a>

## Add a comment to a permit or deny policy

You can add a comment to a permit or deny policy after you add the policy to the configuration. You can then modify and delete comments that you add.

[back to top](#top)

<a name="vma"> </a>

## View and manage IP groups

If a network address set is prefixed with <code>fwcp-</code>, you can add and delete IP addresses from the IP group. If a network address does not have the <code>fwcp-</code> prefix, you can only view the IP group. The address set must contain at least one IP address at all times. You can view updates to address sets in the change log.

To manage editable IP groups with the <code>fwcp-</code> prefix, click the hyperlink for the group you want to manage. In the **manage IP group** dialog box that appears, you can manage addresses and comments from the address set from this window.

To view non-editable IP groups, click the hyperlink for the group that you want to view.

**Note:** For changes to be written to the firewall, click **Commit Changes**.

[back to top](#top)

<a name="mbl"> </a>

## Manage the blacklist

The blacklist is a central area for source IP addresses for which you want to deny access. You can add and delete host IP addresses and IP ranges from the Manage Blacklist menu. All IP addresses listed in the earlier version were migrated to this blacklist. Updates to the blacklist are logged in the change log.

Access the blacklist from the **Manage Blacklist** option in the side navigation bar, as shown in the following image. Customers with view-only permissions have the **View Blacklist** option.

<img src="/knowledge_center/sites/default/files/field/image/926-476-3.png" width="219" height="206" border="1" alt=""  />

Use the **Manage Blacklist** dialog box to add IP addresses to and delete IP addresses from the blacklist, and to add comments.

<img src="" />

**Note:** The blacklist is listed a **FWCP-Customer-Deny Object Group** in earlier versions of the firewall manager.

[back to top](#top)

<a name="vcl"> </a>

## View the Change Log

The Change Log tracks details about each change made in the Firewall Manager, with the exception of comments. It lists the type of change that occurred, the category of the change, details about the change, the user who made the change, and the date the change was made.

**Note:** Changes made directly in the firewall are not displayed in the Change Log.

To access the log, click the **Change Log** tab.

[back to top](#top)

<a name="nat"> </a>

## View static NATs (network address translations)

The **Static NATs** tab displays the public IP address, the private IP address that the public IP address is translated to, and the associated private IP netmask.

<img src="" />

**Note:** If the device is a Cisco ASA using software version 8.3 or later, the static NATs cannot be displayed because they are formatted differently in this version. We will be working to support iOS 8.3 in a future version of the Firewall Manager.

&nbsp;
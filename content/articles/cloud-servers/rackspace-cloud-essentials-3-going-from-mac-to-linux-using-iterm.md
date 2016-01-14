---
node_id: 1225
title: Connecting to Linux from Mac OS X by using Terminal
type: article
created_date: '2011-10-06 05:54:02'
created_by: rose.contreras
last_modified_date: '2015-12-31 15:2109'
last_modified_by: stephanie.fillmon
product: Cloud Servers
body_format: tinymce
---

undefined&rsquo;re connecting as a non-root user,
replace *root* in the instructions with your username.

1.  Go to **Applications** \> **Utilities**, and open **Terminal**.

    ![](/knowledge_center/sites/default/files/field/image/1-FindTerm_1_0.png)

    A terminal window interface is displayed:

        user00241 in ~MKD1JTF1G3->$

2.  Establish an SSH connection to the server by using the following
    syntax:

        ssh root@IPaddress

    Example:

        MKD1JTF1G3->$ ssh root@166.76.69.51

    The first time you connect to your server, a message asks if you
    want to continue connecting. This message appears because your
    server has an RSA key that is not stored in your system registry,
    the identity of which cannot be verified.

        The authenticity of host '198.61.208.131 (198.61.208.131)' can't be established.
        RSA key fingerprint is 47:ff:76:b4:211:0f:11:15:21:bd:92:2f:44:0a:d9:0a.
        Are you sure you want to continue connecting (yes/no)?

3.  Type **yes** and press **Enter**. This action adds the RSA key to
    the list of known hosts. You will not see this warning again during
    future connections.
4.  Enter the root password for this server. The password does not echo
    to the screen.

        MKD1JTF1G3-$ ssh root@198.61.208.131
        root@198.61.208.131's password:

    If you entered the correct password, the prompt responds with a
    shell prompt:

        [root@yourservername ~]#

Change the root password
------------------------

After your first login, change the root password.

1.  At the shell prompt, enter the following command:

        passwd

2.  Change your password, as follows. The password does not echo to the
    screen.

        Enter new UNIX password:
        Retype new UNIX password:

    If the passwords match, you will receive the following confirmation
    that the authentication tokens have been updated successfully:

        Passwd: password updated successfully

Use the new password with the root user when you connect to your server.

Where to go from here
---------------------

The next article shows you how to use [Rescue
Mode](http://www.rackspace.com/knowledge_center/article/managing-your-server-rescue-mode)
to connect to your cloud server, which is useful when you are performing
troubleshooting and when your server becomes unresponsive.

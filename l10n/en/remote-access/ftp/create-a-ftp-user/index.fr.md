+++
url = "/remote-access/ftp/creer-a-user-ftp/"
title = "How to create an FTP user"
layout = "howto"
weight = 30
hidden = true
tags = [ "remote access", "[currency symbol] ftp" ]
+++

In order to connect to your _FTP_account it is necessary to have a user. By default, a user with the name of your _account_ is created at its creation. You can create as many FTP users as you wish that you can administer from your admin interface to the **Remote Access > FTP tab**.

{{< fig "images/admin-panel_list-ftp-users.en.png" "Admin interface: list of FTP users">}}

- Name: FTP user name, prefixed to your account name;
- Password: password associated with the user;
- Root directory: directory in which the user is logged in.

{{< fig "images/admin-panel_add-ftp-user.en.png" "Admin interface: adding FTP user">}}

{{% notice note %}}
FTP offers an insulation : the user will not be able to circulate freely on the parent directories of his root directory.
{{%/notice %}}


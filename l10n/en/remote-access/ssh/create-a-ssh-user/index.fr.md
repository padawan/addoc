+++
url = "/remote-access/ssh/creer-un-user-ssh/"
title = "How to create an SSH user"
layout = "howto"
weight = 30
hidden = true
tags = [ "remote access", "ssh" ]
+++

In order to log in to your _SSH_ account, it is necessary to have a user. By default, a user with the name of your _account_ is created at its creation. You can administer your SSH users from your admin interface, the **Remote Access > SSH** tab.

{{< fig "images/admin-panel_ssh-users-list.png" "Admin interface: list of SSH users">}}

- Name: name of SSH user, prefix of your account name;
- Password: password associated with the user. It is necessary for the first SSH connection; the [key connection](remote-access/ssh/use-keys) can then be used;
- "HOME" directory: directory in which the user arrives at his/her login;
- [Shell](https://fr.wikipedia.org/wiki/Shell_Unix): Your user's command interpreter.

{{< fig "images/admin-panel_ssh-users-add.png" "Admin interface: add SSH user">}}

{{% notice note %}}
Unlike FTP, SSH does not offer any isolation. This will allow the user to circulate freely throughout all the accounts directories.
{{%/notice %}}

{{% notice info %}}
Meme if not recommended for permissions issues on folders and files, you can create as many SSH users as you want.
{{%/notice %}}

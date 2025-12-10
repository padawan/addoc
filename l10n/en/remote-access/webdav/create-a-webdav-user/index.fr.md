+++
url = "/remote-access/webdav/creer-a-user-webdav/"
title = "How to create a WebDAV user"
layout = "howto"
weight = 30
hidden = true
tags = [ "remote access", "webdav" ]
+++

In order to log in to your _WebDAV_ account, it is necessary to have a user. By default, a user with the name of your `[compte]` is created at its creation. You can create as many WebDAV users as you wish that you can administer from your admin interface, the **Remote Access > WebDAV** tab.

{{< fig "images/admin-panel_list-webdav-users.png" "Admin interface: list of WebDAV users">}}

- Name: name of WebDAV user, prefixed to your account name;
- Password: password associated with the user;
- Root directory: directory in which the user is logged in.

{{< fig "images/admin-panel_add-webdav-user.png" "Admin interface: adding WebDAV user">}}

{{% notice note %}}
WebDAV offers insulation: the user will not be able to circulate freely on the parent directories of his root directory.
{{%/notice %}}


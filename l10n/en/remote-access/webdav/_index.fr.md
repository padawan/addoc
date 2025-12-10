+++
url = "/remote/webDAV/"
title = "WebDAV"
weight = 5
tags = [ "remote access", "webdav" ]
archetype = "chapter"
+++

WebDAV, for [Web-based Distributed Authoring and Versioning](http://www.webdav.org/), allows users to collaboratively modify and manage files on remote web servers.

- [API - WebDAV](https://api.alwaysdata.com/v1/webdav/doc/)
- [Create WebDAV user](create-a-webdav-user)

{{% notice info %}}
WebDAV is not active by default on [Cloud Private](accounts/billing/private-cloud-prices) (default ports are used by sites). Contact [support](https://admin.alwaysdata.com/support/add/) if you need it.
{{%/notice %}}

## Login with WebDAV

| Information |                                                                                                                    |
| ----------- | ------------------------------------------------------------------------------------------------------------------ |
| Hostels     | webdav-[compte].alwaysdata.net |
| Ports       | 80 (HTTP) or 443 (HTTPS)                                                     |
| Username    | associated user and password                                                                                       |

{{< fig "admin-panel_list-webdav-users.png" "Admin interface: list of WebDAV users" >}}

### With Windows

1. Right-click on the icon **Workstation** or **Computer**;
2. Choose **Connect a network drive**. In the _Folder_ field, say:
   - on Vista and Superiors: `https://webdav-[compte].alwaysdata.net/`
3. Click _Login_ under a different username and enter your credentials. Confirm and click _Finish_.

### With Mac OS X

1. In the **Finder**, choose _Go > Connect to Server_;
2. In the _Server Address_ field, enter `http://webdav-[compte].alwaysdata.net/`;
3. Click _Login_.

### With davfs2 (Linux)

**davfs2** has the advantage of mounting WebDAV shares as a local partition, so having its files accessible from any application. To mount a partition in `/mnt/alwaysdata`:

```sh
$ sudo mount.davfs https://webdav-[compte].alwaysdata.net/ /mnt/alwaysdata
```

{{% notice note %}}
Replace `webdav-[compte].alwaysdata.net` with your WebDAV host-name, available in **Remote Access > WebDAV**.
{{%/notice %}}


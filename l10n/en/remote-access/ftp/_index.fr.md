+++
url = "/remote/ftp/"
title = "FTP"
weight = 5
tags = [ "remote access", "[currency symbol] ftp" ]
archetype = "chapter"
+++

FTP, for [File Transfer Protocol](https://fr.wikipedia.org/wiki/File_Transfer_Protocol) is a protocol for sharing files on a remote network.

- [API - FTP](https://api.alwaysdata.com/v1/ftp/doc/)
- [Create FTP User](create-a-ftp-user)
- [Download files with FileZilla](use-filezilla)
- [Freight issues](remote-access/ftp/troubleshooting)

## Connect to FTP

| Information    |                                                                                                                     |
| -------------- | ------------------------------------------------------------------------------------------------------------------- |
| Hostels        | **ftp-[compte].alwaysdata.net** |
| Port           | **990 (SSL/TLS)**                                                                                |
| Alternate Port | 21 (STARTTLS)                                                                                    |
| Username       | **user** and **password** associated                                                                                |

{{< fig "admin-panel_list-ftp-users.en.png" "Admin interface: list of FTP users" >}}

{{% notice note %}}
Replace `ftp-[compte].alwaysdata.net` with your FTP host-name.
{{%/notice %}}

Maximum simultaneous connections per user is _10_. It is possible to change it in Private Cloud environments.

## ftpaccess

It is possible to create [.ftpaccess]files (http://www.proftpd.org/docs/howto/ftpaccess.html) to change the FTP configuration of the relevant folders.

### Example: Block read-only access to a user

Create a `.ftpaccess` at the root of the folder with the following directive:

```sh
<Limit WRITE>
DenyUser [FTP user]
</Limit>
```

## Misc

The port range used for passive mode is _53000-53999_.

---

- [FileZilla](https://filezilla-project.org/download.php): Free FTP client

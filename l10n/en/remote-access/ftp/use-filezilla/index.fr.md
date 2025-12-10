+++
url = "/remote/ftp/user-filezilla/"
title = "How to upload files with FileZilla"
layout = "howto"
tags = [ "files", "filezilla", "[currency symbol] ftp" ]
hidden = true
+++

[Login Information Reminder](remote-access/ftp#se-connecter-en-ftp)

[FileZilla](https://filezilla-project.org/) is a free working FTP client on all operating systems.

In our example we use the `test` account and its main FTP user. This is to be replaced by your personal login information.

- Go to **Files > Site Manager > New Site**

{{< fig "images/site-manager.en.png" "" >}}

- Fill in your login details (hostname, ID and port) and then click **Connect**
- Enter your password

{{< fig "images/password.en.png" "" >}}

- The connection is done and you only have to drag and drop from the **Local Site** directory to the **Remote Site** directory.

{{< fig "images/interface.png" "" >}}

Put the files directly into the `www` directory.

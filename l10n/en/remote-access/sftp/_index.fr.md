+++
url = "/remote/sftp/"
title = "SFTP"
weight = 5
tags = [ "remote access", "sftp" ]
archetype = "chapter"
+++

The SFTP protocol (for [SSH File Transfer Protocol](https://fr.wikipedia.org/wiki/SSH_File_Transfer_Protocol)) allows to secure an FTP transfer through an SSH tunnel. Users can thus use a simple graphical interface via the FTP client of their choice.

## Sign in as SFTP

In **Remote Access > SSH** allow _password login_ to your SSH user.

{{< fig "admin-panel_ssh-users-list.en.png" "Admin interface: list of SSH users">}}

Then fill in your FTP client the SSH login information. Let's take the example of the _test_ account and the FTP client [FileZilla](https://filezilla-project.org/):

- user: `test`
- password
- hostname: `ssh-test.alwaysdata.net`
- port: `22`

{{< fig "filezilla_sftp-connection.png" "FileZilla interface: SFTP connection" >}}

## Misc

As with the SSH protocol, SFTP users are not `chroot`. Nevertheless it is possible to limit their actions by choosing the **SFTP only** shell.

It must not be confused with the [FTPS]protocol (remote-access/ftp): FTP transfer secured by SSL or TLS protocols.

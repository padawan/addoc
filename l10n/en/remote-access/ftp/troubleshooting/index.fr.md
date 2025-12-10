+++
url = "/remote-access/ftp/frequent-issues/"
title = "FTP - Problems"
layout = "faq"
weight = 50
hidden = true
tags = [ "remote access", "troubleshooting", "[currency symbol] ftp" ]
+++

## Login

A [IP block] (security/network) occurs after about ten failed attempts to connect to the server.

{{% notice info %}}
alwaysdata has login logs from which you can exceptionally request a copy.
{{%/notice %}}

### 530 Home Directory does not exist

Please make sure the root directory specified in **Remote Access > FTP** exists. If you are not superior, enter the root of the account: `/`.

This error may have other reasons and, in particular, appear sporadically. Try logging in again or contact [support](https://admin.alwaysdata.com/support/add).

### Answer: 530 Login or password incorrect

The login/password pair is not good check it or change your password in **Remote Access > FTP**.

### ECONNREFUSED - Connection denied by server / ECONNRESET - Connection reset by peer

The connection is blocking before reaching alwaysdata servers, please:

- if you are in **active** or **passive**: in active mode the FTP server will set the port to use and initialize the connection, while in passive mode it is the FTP client that initializes the connection. The latter is therefore preferred;
  - For **FileZilla** go to _Edit > Settings > Login > FTP_.
- that you do not have any firewall software;
- by switching device;
- changing internet connection.

If none of these solutions works, try the [SFTP]connection (remote-access/sftp).

{{% notice info %}}
Schools and Hotel’s Wi-Fi connections often block such services.
{{%/notice %}}

### ECONNABORTED - Connection canceled

FTP connection is performed with an IP but another IP then connects in passive mode. Be sure to use only one IP during the entire FTP connection.
If you can't fix this behavior, you can try the [SFTP]connection (remote-access/sftp).

## Access files

### Some files are not visible

Cache directories and files, such as `.htaccess`, are not forcefully visible by default; this is a **option for your FTP client**.

For **FileZilla** go to _Server > Force cached files.


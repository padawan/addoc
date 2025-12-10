+++
url = "/remote-access/connection-information/"
title = "Login information"
linkTitle = "Login information"
layout = "faq"
weight = 1
tags = [ "account", "technical environment" ]
+++

The subdomain assigned to you when creating your account ends with the **.net** extension and not _.com_ like other alwaysdata domains.

Whenever you encounter the shape `*-[compte].alwaysdata. and`, you must replace `[compte]` with the name of your account, chosen when creating it.

| Functionality      | Information                                                                                                                                                                                                                         |
| :----------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Administration** |                                                                                                                                                                                                                                     |
| URL                | https://admin.alwaysdata.com                                                                                                                                                        |
|                    | Email/password, [Possible Double Authentication](security/two-factor-authentication)                                                                                                                                                |
| API                | [api.alwaysdata.com/v1](api) (submitted to a _[rate limit](api/usage#rate-limit)_)                                                                                               |
|                    | [Tokens](accounts/tokens) available via _Profile_                                                                                                                                                                                   |
| **Geometrics**     |                                                                                                                                                                                                                                     |
| DNS                | Primary: dns1.alwaysdata.com                                                                                                                                                        |
|                    | Secondary: dns2.alwaysdata.com                                                                                                                                                      |
| MX                 | Primary: mx1.alwaysdata.com (TTL: 10)                                                                                                            |
|                    | Secondary: mx2.alwaysdata.com (TTL: 20)                                                                                                          |
|                    | if [Private Cloud](accounts/billing/private-cloud-prices): [serveur].alwaysdata.net (TTL: 5) |
| **Databases**      |                                                                                                                                                                                                                                     |
| MySQL              | host: mysql-[compte].alwaysdata.net                                                                                             |
|                    | Port: 3306                                                                                                                                                                                                          |
|                    | Admin interface: [phpMyAdmin](https://phpmyadmin.alwaysdata.com)                                                                                                                                                    |
| PostgreSQL         | Hoest: postgresql-[compte].alwaysdata.net                                                                                       |
|                    | Port: 5432                                                                                                                                                                                                          |
|                    | Admin interface: [phpPgAdmin](https://phppgadmin.alwaysdata.com)                                                                                                                                                    |
| RabbitMQ           | Hoest: rabbitmq-[compte].alwaysdata.net                                                                                         |
|                    | Port: 5672                                                                                                                                                                                                          |
| Redis              | Hosted: localhost or 127.0.0.1                                                                                                                                      |
|                    | Port: 6380                                                                                                                                                                                                          |
| Memcached          | Hosted: localhost or 127.0.0.1                                                                                                                                      |
|                    | Port: 11211                                                                                                                                                                                                         |
| **Emails**         |                                                                                                                                                                                                                                     |
| Webmail            | [RoundCube](https://webmail.alwaysdata.com)                                                                                                                                                                                         |
| Mailing lists      | [Mailman](https://mailman.alwaysdata.com)                                                                                                                                                                                           |
| IMAP               | host: imap-[compte].alwaysdata.net                                                                                              |
|                    | Ports: 993 (SSL/TLS)                                                                                                                                                                             |
| POP3               | Hostep: pop-[compte].alwaysdata.net                                                                                             |
|                    | Ports: 995 (SSL/TLS)                                                                                                                                                                             |
| SMTP               | Hostep: smtp-[compte].alwaysdata.net                                                                                            |
|                    | Ports: 465 (SSL/TLS)                                                                                                                                                                             |
|                    | Login: Required (email address and associated password)                                                                                                                                          |
| **Remote access**  |                                                                                                                                                                                                                                     |
| FTP                | host: ftp-[compte].alwaysdata.net                                                                                               |
|                    | Port: 990 (SSL/TLS)                                                                                                                                                                              |
| SFTP               | Hoest: ssh-[compte].alwaysdata.net                                                                                              |
|                    | Port: 22                                                                                                                                                                                                            |
| SSH                | Hoest: ssh-[compte].alwaysdata.net                                                                                              |
|                    | Port: 22                                                                                                                                                                                                            |
|                    | Web access (via Shell in a box): https://ssh-[compte].alwaysdata.net                         |
| WebDAV             | host: webdav-[compte].alwaysdata.net                                                                                            |
|                    | Port: 80                                                                                                                                                                                                            |
| **Services**       |                                                                                                                                                                                                                                     |
|                    | host: services-[compte].alwaysdata.net                                                                                          |
|                    | Ports: between 8300 and 8499                                                                                                                                                                                        |

{{% notice note %}}
The default login matches - with the exception of the emails for which the login is the email address - to the **account name** and its password is the one indicated at the account creation. All passwords are encrypted - and therefore not recoverable - but can be changed in the generated menus.
{{%/notice %}}

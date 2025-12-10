+++
url = "/domaines/utiliser-des-mx-externes/"
title = "How to use an external mail server"
linkTitle = "Use external MX"
layout = "howto"
weight = 20
tags = [ "dns", "domain", "email" ]
+++

To use another provider's mail server, change [MX records](https://fr.wikipedia.org/wiki/Enregistrement_Mail_eXchanger). They determine the receiving server of an electronic mail.

1. {{< fig "images/admin-panel_dns-record-list.png" "Administration interface: list of DNS records" >}}
2. Choose **Add DNS record**;
3. {{< fig "images/admin-panel_add-mx.en.png" "Admin interface: add MX record" >}}

This will automatically disable our MX recordings.

{{% notice warning %}}
Do not put the root in **Host Name**. For example, by specifying _example.org_ in this box, you will create a record for _example.org.example.org_.
{{%/notice %}}

{{% notice note %}}
A record with `@` as host name for some providers matches the empty subdomain. In our case, the **Host Name** box should be empty.
{{%/notice %}}

## MX servers of different providers

| Provider          | TTL   | Priority | Value                                                                                                                                                                                                       |
| ----------------- | ----- | -------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Gandi             | 10800 | 10       | spool.mail.gandi.net                                                                                                                                        |
|                   | 10800 | 50       | fb.mail.gandi.net                                                                                                                                           |
| GSuite            | 3600  | 1        | aspmx.l.google.com                                                                                                                                          |
|                   | 3600  | 5        | alt1.aspmx.l.google.com                                                                                                                     |
|                   | 3600  | 5        | alt2.aspmx.l.google.com                                                                                                                     |
|                   | 3600  | 10       | alt3.aspmx.l.google.com                                                                                                                     |
|                   | 3600  | 10       | alt4.aspmx.l.google.com                                                                                                                     |
| Microsoft Outlook | 3600  | 1        | [id_mx_microsoft].mail.protection.outlook.com |
| OVH               | 3600  | 1        | mx0.mail.ovh.net                                                                                                                                            |
|                   | 3600  | 5        | mx1.mail.ovh.net                                                                                                                                            |
|                   | 3600  | 50       | mx2.mail.ovh.net                                                                                                                                            |
|                   | 3600  | 100      | mx3.mail.ovh.net                                                                                                                                            |

{{% notice note %}}
[id_mx_microsoft] is randomly managed by Microsoft by the domain name
{{% /notice %}}

## Override MX servers

It can be useful to short-circuit external MX to reach alwaysdata MX.

To send an email to `foobar@example.org` via the MX alwaysdata (while the MX from `example.org` is external):

- create [email address](e-mails/create-an-e-mail-address) on the admin interface;
- send an email to:
  - `foobar%example.org@mx.alwaysdata.com` if the account is on the Public Cloud;
  - `foobar%example.org@server.alwaysdata.com` if the account is on a Private Cloud (`server` should be replaced by the server name).

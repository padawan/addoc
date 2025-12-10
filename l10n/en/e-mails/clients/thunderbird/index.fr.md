+++
url = "/emails/clients/thunderbird/"
title = "How to configure Thunderbird"
layout = "howto"
tags = [ "email", "Thunderbird", "Mozilla" ]
hidden = true
+++

## General

{{% notice tip %}}
For domains using our DNS servers, Thunderbird _autoconfiguration_ is usable. All you have to do is enter your username and password. Other parameters are automatically managed.
{{%/notice %}}

| Server   | Service | Information           |                                                                                                                    |
| -------- | ------- | --------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Incoming | IMAP    | Host Name             | imap-_[compte]_.alwaysdata.net |
|          |         | Port                  | 993                                                                                                                |
|          |         | Connection security   | Will be automatically chosen                                                                                       |
|          |         | Authentication Method | Normal Password                                                                                                    |
|          |         | Username              | Your email address - e.g. _contact\@example.org_     |
|          |         | Password              | Your email address password                                                                                        |
|          | POP3    | Host Name             | pop-_[compte]_.alwaysdata.net  |
|          |         | Port                  | 995                                                                                                                |
|          |         | Connection security   | Will be automatically chosen                                                                                       |
|          |         | Authentication Method | Normal Password                                                                                                    |
|          |         | Username              | Your email address - e.g. _contact\@example.org_     |
|          |         | Password              | Your email address password                                                                                        |
| Outgoing | SMTP    | Host Name             | smtp-_[compte]_.alwaysdata.net |
|          |         | Port                  | 465                                                                                                                |
|          |         | Connection security   | Will be automatically chosen                                                                                       |
|          |         | Authentication Method | Normal Password                                                                                                    |
|          |         | Username              | Your email address - e.g. _contact\@example.org_     |
|          |         | Password              | Your email address password                                                                                        |

_`[compte]`_ must be replaced with your account name and _`contact@example.org`_ with your email address. They are defined in the **Emails > Addresses** menu of our admin interface.

## Screenshots

In our example we will have the following information (to replace with your personal login information):

- Account name: `test`
- Email address: `test@alwaysdata.net`

Go to **Accounts > Set up an Account: E-Mail**.

{{< fig "images/thunderbird_new-account.en.png" "Thunderbird: Create an account" >}}

To edit it once created, go to **Accounts > View settings for this account** or in the **Edit > Account Settings**:

- {{< fig "images/thunderbird_imap-settings.en.png" "Thunderbird: Incoming server settings" >}}
- {{< fig "images/thunderbird_smtp-settings.png" "Thunderbird: Outgoing server settings" >}}

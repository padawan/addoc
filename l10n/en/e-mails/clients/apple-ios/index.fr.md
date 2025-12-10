+++
url = "/emails/clients/apple-ios/"
title = "How to configure Mail (Apple/iOS)"
layout = "howto"
tags = [ "email", "ios", "macos", "apple" ]
hidden = true
+++

In our examples we will have the following information:

- Account name: `test`
- Email address: `test@alwaysdata.net`

They are to be replaced with your personal login information:

| Server   | Service | Information           |                                                                                                                    |
| -------- | ------- | --------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Incoming | IMAP    | Host Name             | imap-_[compte]_.alwaysdata.net |
|          |         | Port                  | 993                                                                                                                |
|          |         | Username              | Your email address - e.g. _contact\@example.org_     |
|          |         | Password              | Your email address password                                                                                        |
|          |         | Authentication Method | Normal Password                                                                                                    |
|          | POP3    | Host Name             | pop-_[compte]_.alwaysdata.net  |
|          |         | Port                  | 995                                                                                                                |
|          |         | Username              | Your email address - e.g. _contact\@example.org_     |
|          |         | Password              | Your email address password                                                                                        |
|          |         | Authentication Method | Normal Password                                                                                                    |
| Outgoing | SMTP    | Host Name             | smtp-_[compte]_.alwaysdata.net |
|          |         | Port                  | 465                                                                                                                |
|          |         | Username              | Your email address - e.g. _contact\@example.org_     |
|          |         | Password              | Your email address password                                                                                        |
|          |         | Authentication Method | Normal Password                                                                                                    |

{{% notice tip %}}
_[compte]_ must be replaced with your account name and _contact\@example.org_ with your email address. They are defined in the **Emails > Addresses** menu of our admin interface.
{{%/notice %}}

## MacOS: Mail app

Go to **File > Add Account > Other Mail Account...**

- Specify the login details and choose between IMAP or POP for _Incoming_ mail;
- If you receive an SSL error message, click **Connect** anyway, you can then re-enter the login information.

Leave password authentication.

## iOS (iPhone, iPad): Mail app

{{< fig "images/mail_ipad.en.png" "Mail on mobile" >}}

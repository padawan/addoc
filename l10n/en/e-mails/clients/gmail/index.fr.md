+++
url = "/emails/clients/gmail/"
title = "How to configure Gmail"
layout = "howto"
hidden = true
tags = [ "email", "gmail" ]
+++

In our examples we will have the following information:

- Account name: `test`
- Email address: `test@alwaysdata.net`

They are to be replaced with your personal login information:

| Server   | Service | Information |                                                                                                                    |
| -------- | ------- | ----------- | ------------------------------------------------------------------------------------------------------------------ |
| Incoming | IMAP    | IMAP Server | imap-_[compte]_.alwaysdata.net |
|          |         | Username    | Your email address - e.g. _contact\@example.org_     |
|          |         | Password    | Your email address password                                                                                        |
|          |         | Port        | 993                                                                                                                |
| Outgoing | SMTP    | SMTP Server | smtp-_[compte]_.alwaysdata.net |
|          |         | Username    | Your email address - e.g. _contact\@example.org_     |
|          |         | Password    | Your email address password                                                                                        |
|          |         | Port        | 465                                                                                                                |

{{% notice tip %}}
_[compte]_ must be replaced with your account name and _contact\@example.org_ with your email address. They are defined in the **Emails > Addresses** menu of our admin interface.
{{%/notice %}}

## Mobile

Go to **Settings > Add Account > Other**.

{{< fig "images/gmail_mobile_en.png" "Gmail on mobile" >}}

- For _outgoing mail_, check the **Require connection** box.

## Web Browser

### Incoming mail

Since [POP connections](https://support.google.com/mail/answer/16604719) have not been supported by Gmail, its webmail can only be used for sending mails. Otherwise you need to go through their Google Workspace or an [redirection](/e-mails/create-an-e-mail-address#redirection) to your Gmail address.

### Outgoing mail (SMTP)

Go to **Settings > Accounts and import**.

{{< fig "images/gmail_interface_en.png" "Gmail: Interface" >}}
{{< fig "images/gmail_interface2_en.png" "Gmail: Account Settings" >}}

Go to **Add another email address**.

- Uncheck the box **Treat as an alias**.

{{< fig "images/gmail_add-smtp_en.png" "Gmail: create SMTP account" >}}
{{< fig "images/gmail_add-smtp-final_en.png" "Gmail: create SMTP account - result" >}}

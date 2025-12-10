+++
url = "/emails/clients/outlook/"
title = "How to configure Outlook"
layout = "howto"
tags = [ "email", "outlook", "microsoft" ]
hidden = true
+++

## General

{{% notice tip %}}
For domains using our DNS servers, Outlook _autoconfiguration_ is usable. All you have to do is enter your username and password. Other parameters are automatically managed.
{{%/notice %}}

| Server   | Service | Information           |                                                                                                                    |
| -------- | ------- | --------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Incoming | IMAP    | Server                | imap-_[compte]_.alwaysdata.net |
|          |         | Port                  | 993                                                                                                                |
|          |         | Encryption method     | Will be automatically chosen                                                                                       |
|          |         | Authentication Method | Require secure password authentication (SPA) when logging in                                    |
|          |         | Mail Address          | Your email address - e.g. _contact\@example.org_     |
|          |         | Password              | Your email address password                                                                                        |
|          | POP3    | Server                | pop-_[compte]_.alwaysdata.net  |
|          |         | Port                  | 995                                                                                                                |
|          |         | Encryption method     | Will be automatically chosen                                                                                       |
|          |         | Authentication Method | Require secure password authentication (SPA) when logging in                                    |
|          |         | Mail Address          | Your email address - e.g. _contact\@example.org_     |
|          |         | Password              | Your email address password                                                                                        |
| Outgoing | SMTP    | Server                | smtp-_[compte]_.alwaysdata.net |
|          |         | Port                  | 465                                                                                                                |
|          |         | Encryption method     | Will be automatically chosen                                                                                       |
|          |         | Authentication Method | Require secure password authentication (SPA) when logging in                                    |
|          |         | Mail Address          | Your email address - e.g. _contact\@example.org_     |
|          |         | Password              | Your email address password                                                                                        |

_`[compte]`_ must be replaced with your account name and _`contact@example.org`_ with your email address. They are defined in the **Emails > Addresses** menu of our admin interface.

## Screenshots

In our example we will have the following information (to replace with your personal login information):

- Account name: `test`
- Email address: `test@alwaysdata.net`

### Computer

Go to **Files > Information > Add Account**.

{{< fig "images/outlook_desktop_interface2_en.png" "Outlook: messaging interface" >}}
{{< fig "images/outlook_desktop_interface1_en.png" "Outlook: Files menu" >}}

{{< fig "images/outlook_desktop_en.png" "Outlook: Add Account" >}}

- Set up account manually;
- Choose between POP and IMAP;
- Check the **Require Secure Password Authentication (SPA) checkboxes on login**.

### Mobile

Go to **Let's go > Ignore** if we offer account types **> IMAP Advance** or **POP3**.

{{< fig "images/outlook_mobile_en.png" "Outlook on mobile" >}}

Click **Advanced** to specify _host names_.

+++
url = "/emails/use e-email/"
title = "How to view an email address"
linkTitle = "Check email address"
layout = "howto"
weight = 10
tags = [ "email" ]
+++

It is possible to view your emails in several ways. Here are the two most common ones.

## Email Client

If you want to set up an email software on your computer, or any other device, here is the information you will need to complete.

| Server   | Service                                                                | Information                                                                                                                                 |
| -------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Incoming | [IMAP](https://fr.wikipedia.org/wiki/Internet_Message_Access_Protocol) | Hoest: **imap-[compte].alwaysdata.net** |
|          |                                                                        | Port: **993 (SSL/TLS)**                                                                                  |
|          |                                                                        | Alternative port: 140 (STARTTLS)                                                                         |
|          |                                                                        | Username: **email address** and **password** associated                                                                     |
|          | [POP3](https://fr.wikipedia.org/wiki/Post_Office_Protocol)             | Hoest: **pop-[compte].alwaysdata.net**  |
|          |                                                                        | Port: **995 (SSL/TLS)**                                                                                  |
|          |                                                                        | Alternate port: 110 (STARTTLS)                                                                           |
|          |                                                                        | Username: **email address** and **password** associated                                                                     |
| Outgoing | [SMTP](https://fr.wikipedia.org/wiki/Simple_Mail_Transfer_Protocol)    | Hoest: **smtp-[compte].alwaysdata.net** |
|          |                                                                        | Port: **465 (SSL/TLS)**                                                                                  |
|          |                                                                        | Alternate port: 587 (STARTTLS)                                                                           |
|          |                                                                        | Username: **email address** and **password** associated                                                                     |

{{% notice note %}}
You need to replace [compte] with the name of your account, chosen at the time of creation.
{{%/notice %}}

Password authentication is **required** to use our SMTP server, enter the same credentials as for the incoming server.

It is also possible to use the SMTP server of your Internet provider.

- [Configure Apple/iOS](e-mails/clients/apple-ios)
- [Configure Gmail](e-mails/clients/gmail)
- [Configure Mozilla Thunderbird](e-mails/clients/thunderbird)
- [Configure Outlook](e-mails/clients/outlook)

## Webmail

If you want to check your drink from a browser, we put at your disposal [our webmail, Roundcube](https://webmail.alwaysdata.com). Log in with the email address you want to view and its associated password.

By default, the webmail uses the user's web browser language (that of its first login). To switch languages, click **Settings** in the upper right corner, then **User Interface > Language**.

{{< fig "images/roundcube_change-parameter-1.en.png" "Webmail: change settings - step 1" >}}

{{< fig "images/roundcube_change-parameter-2.en.png" "Webmail: Change Settings - Step 2" >}}

{{% notice tip %}}
If you change your password via the webmail, you will need to log out and log in again.
{{%/notice %}}

## Feedback

- Emails are kept in [Maildir]format (https://fr.wikipedia.org/wiki/Maildir) in the `$HOME/admin/mail` directory;
- If the recipient MX server is not available, the email will be kept for a maximum length of 5 days with regular redirection attempts;
- The size limit of emails sent is set to **50 MB**;
- SMTP authentication is not necessary in case of a hosted service on alwaysdata servers (e.g. website or scheduled task).

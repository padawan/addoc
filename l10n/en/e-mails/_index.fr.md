+++
url = "/emails/"
title = "Emails"
pre = "<i class='fas fa-fw fa-paper-plane'></i> "
weight = 15
archetype = "chapter"
tags = [ "email" ]
+++

We provide SMTP, IMAP and POP3 accesses, which are listed in the **Emails > Addresses** menu. If not from our servers directly (e.g. from an HTTP application), it is _necessary_ to authenticate with an email address to send emails.

Our email servers are common; we use [Exim](https://www.exim.org/) and [Dovecot](https://www.dovecot.org/).

You can [create an email address](create-an-e-mail-address) in the **Emails > Addresses** tab of your alwaysdata administration interface and [check your emails](use-an-e-mail-address) via an email client of your choice or our [webmail](https://webmail.alwaysdata.com).

From the moment the email address is created, it will be possible to send emails via our SMTP servers. To receive it, the domain must have [MX DNS records](https://fr.wikipedia.org/wiki/Enregistrement_Mail_eXchanger). To use our email servers specify `mx1.alwaysdata.com` and `mx2.alwaysdata.com`.

- [Mailing Lists](mailing-lists)

## Resources

- [API](https://api.alwaysdata.com/v1/mailbox/doc/)
- [Add multiple email addresses using CSV](create-mailboxes-using-csv)

* [Add filtering regeneration](add-a-filter-rule)
* [Use Sieve scripts](use-sieve-scripts)
* [Receipt White List](e-mails/whitelist)

- [Change provider](./transfer-in)
- [Use external MX](domains/use-external-mx)
- [SMTP Relay](e-mails/smtp-relay)

* [Deliverable: best practices](delivery)
* [Configure SPF/DKIM/DMARC](set-up-spf-dkim-dmarc)
* [Check email sending](check-email-sending)
* [SMTP Queue](smtp-queue)
* [Read source email](read-an-e-mail-source)
* [React to spam sending](react-to-spam-mailing)

- [Restore emails](backups/restore-e-mails)
- [Sender Rewriting Scheme](srs)
- [Catch-all](./catch-all)
- [Miscellaneous Questions](./misc)

## Email Clients

- [iOS](clients/apple-ios)
- [Gmail](clients/gmail)
- [Outlook](clients/outlook)
- [Thunderbird](clients/thunderbird)

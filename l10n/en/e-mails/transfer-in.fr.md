+++
url = "/emails/migrer-des-adreses-email-chez-alwaysdata/"
title = "Migrate email addresses to alwaysdata"
layout = "howto"
hidden = true
tags = [ "email" ]
+++

Here's how to migrate email addresses to alwaysdata.

1. [Create email addresses](e-mails/create-an-e-mail-address) on your admin interface, **Emails > Addresses**;

2. Migrate emails already at the current provider via **Emails > Addresses > Edit [example@example.org] - ⚙️ > Import emails**.

This import is done with classic [IMAP]authentication (https://fr.wikipedia.org/wiki/Internet_Message_Access_Protocol) You must therefore know the host name, the user and the password of the email address to be imported. Some services do not allow to use a standard IMAP direct access. You can then:

- follow the following documentations: [Gmail](https://imapsync.lamiral.info/FAQ.d/FAQ.Gmail.txt) and [Office 365](https://imapsync.lamiral.info/FAQ.d/FAQ.Office365.txt);
- or make exports/imports via an email client.

3. Change MX records, to use alwaysdata servers: `mx1.alwaysdata.com` and `mx2.alwaysdata.com`.

This migration can be coupled with a [website migration](sites/transfer-in) or [domain transfer] (domains/transfer-a-domain).

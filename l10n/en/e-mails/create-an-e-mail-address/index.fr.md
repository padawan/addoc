+++
url = "/emails/creer-une-email/"
title = "How to create an email address"
linkTitle = "Create email address"
layout = "howto"
weight = 1
tags = [ "email", "redirect" ]
+++

From the **Emails > Addresses** section of the administration you can create email boxes (provided you added a [domain name](/domains)).

{{< fig "images/admin-panel_mailbox-list.en.png" "Admin interface: List of email boxes" >}}

You will then have a set of fields to fill in. Here are the clarifications.

## Required information

{{< fig "images/admin-panel_create-mailbox_required-info.png" "Admin interface: Emails - required information" >}}

- _Domain_ : domain name of the address to be created;
- _Local part_ : left side of the _@_ email address (for example, if you want to create `contact@example.org`, the local part will be `contact`). You can also create a [catch-all address](e-mails/catch-all).
- _Password_ : Password required for login to this email address.

## Antispam

The antispam used to filter unwanted e-mail ads (_spam_) is free software [Rspamd](https://rspamd.com/).

{{% notice warning %}}
The parameter antispam is the antispam of incoming emails. Emails from our servers necessarily pass through a non-parametric antispam.
{{%/notice %}}

{{< fig "images/admin-panel_mailbox_antispam.png" "Admin interface: Emails - Antispam" >}}

- _Score_ : Anti-spam gives each message a score according to the probability that it is a spam. Messages exceeding this score will be stored in a folder. The lower the score, the greater the possibility of an email being marked as spam, it is therefore preferable to leave the default value;
- _Folder_ : folder where spam will be moved. Default folder is `Spam`;
- _Score from spam to delete_ : messages exceeding this score will be deleted directly, without even being stored in the spam folder. Unless you know what you are doing, leave the value by default.

Antivirus [ClamAV](http://www.clamav.net/) is included with Rspamd to filter potentially infected electronic mail.

## Purging folders

{{< fig "images/admin-panel_mailbox_purge.en.png" "Admin interface: Emails - Purge folders" >}}

- _Hard of retention_ : after this hard work, messages will be permanently deleted;
- _Folders_ : list of folders to purge (separated by a space).

{{% notice note %}}
This feature is relevant when using antispam and/or antivirus : it's your initiative to clear their folders regularly.
{{%/notice %}}

## Redirect

{{< fig "images/admin-panel_mailbox_redirection.en.png" "Admin interface: Emails - Redirect" >}}

- _Addresses_ : addresses to which emails will be redirected (separated by a space);
- _Local copy_ : by checking this box, all redirected emails will also be copied to this email box. Otherwise emails will not be stored, only redirected.
  - If this checkbox is not checked, we created an [alias](https://fr.wikipedia.org/wiki/Alias_\(adresse_%C3%A9lectronique\)).

{{% notice note %}}
If you are using antivirus and/or antispam, emails will never be redirected, to avoid relaying these bad messages to external providers.
{{%/notice %}}

{{% notice warning %}}
Alwaysdata mail servers are not forcefully authorized by the sender's authentication servers (SPF, DKIM, DMARC). This can block redirects.
{{%/notice %}}

## Auto answer

{{< fig "images/admin-panel_mailbox_responder.png" "Admin interface: Emails - Autoresponder" >}}

- _Repeat freely_ : only one automatic message per address will be sent for the duration of this period (in days);
- _Subject_ : automatic post subject;
- _Message_ : automatic message body.

## Quota

{{< fig "images/admin-panel_mailbox_quota.en.png" "Admin interface: Emails - Quota" >}}

- _Size_ : Maximum email box size, in MB (if this quota is reached, new messages will be refused).

{{% notice note %}}
Without precision of the maximum size of an email box, it is the available space of the pack that will act as a ceiling.
{{%/notice %}}

## Sieve Script

{{< fig "images/admin-panel_mailbox_sieve.png" "Admin interface: Emails - Sieve Script" >}}

This technology makes it possible to perform [more precise steps](e-mails/use-sieve-scripts) to receive your messages. If you activate the Sieve script, then its execution will take place after all the steps configured on the creation form of your email box.

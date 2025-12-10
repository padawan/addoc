+++
url = "/emails/delivrabilite-bonnes-pratiques/"
title = "How to improve email delivery"
linkTitle = "Deliverable: best practices"
layout = "howto"
weight = 20
tags = [ "email" ]
+++

Whether your email addresses are hosted in a public cloud or a dedicated environment, delivery of your messages is important and can be optimized through joint work of the host and its users.

## Sender

- Check the name of the sender and send email address;
- Use [identification protocols](e-mails/set-up-spf-dkim-dmarc);
- The _ENVELOPE FROM_ must match the _FROM/HEADER FROM_ in your headers.

## Recipients

- Delete non-existent or inactive addresses;
- Check for spelling errors in addresses;
- Avoid mass shipment;
- Enter the email addresses in the `Cc` (or `Cci`) field rather than one after another in the `To` field (To) when sending a group.

## Content

- Avoid:
  - HTML;
  - use too much punctuation in continuation;
  - to write in red;
  - to write uppercase;
  - using [spam words](https://www.pme-web.com/wp-content/uploads/2014/08/Emailing-Guide-Ultime-des-Mots-Interdits-PME-Web.pdf).
- Heal the subject of the email.

## Email

Make sure good practices are followed by answering "yes" to the following questions:

- Has the recipient explicitly agreed to receive these emails?
- Is a signup link available, easily identifiable and functional?

## Rating System

In order to avoid abuse and optimize delivery of emails sent by its servers, alwaysdata has set up a rating system that is based on different scripts, such as content analysis and forwarding speed.

The lower the note the better the email will be recorded and the sending accepted. On the Public Cloud, any email with a higher rating at _3_ will be blocked. In [Private Cloud] (accounts/billing/private-cloud-prices), the default value is _5_ and you can change it in the **SMTP > Parameters** tab of your server. It is not possible to disable it.

{{% notice note %}}
This note is only used for sending our servers. It does not affect the management of the message at the recipient server level.
{{%/notice %}}

Depending on this rating, the message will be sent via an IP address with a more or less good reputation. This way, by optimizing the quality of your emails and their sending, you will have less chance of your message becoming undesirable.

This system uses [Rspamd](https://rspamd.com/) and an own set of alwaysdata.

In order to avoid abuse of other users on the same mail server you can rent a [dedicated IP](advanced/dedicated-ip-addresses) in the \*\*Advanced> IP Addresses tab of the account. You will be able to specify the emails sent by this IP depending on the note they have received from the antispam.

## Feedback

- The size limit for emails sent is set to **50 MB**.

---

Test deliverable: [Mail test](https://www.mail-tester.com/?lang=fr), [Experte.com](https://www.experte.com/fr/spam-checker)

+++
url = "/emails/srs/"
title = "Sender Rewriting Scheme"
layout = "man"
tags = [ "email", "redirect" ]
hidden = true
+++

[Sender Rewriting Scheme](https://en.wikipedia.org/wiki/Sender_Rewriting_Scheme) (or SRS) allows you to rewrite the address of the editor on the email envelope to bypass blocks [SPF](https://fr.wikipedia.org/wiki/Sender_Policy_Framework)[^1] and thus improve delivery of emails **with redirection**.

{{< fig "images/srs.en.png" "" >}}

## Activation at alwaysdata

To enable it, go to the **Emails > Addresses menu > Edit [email address] - ⚙️ > Redirect > Use SRS**

{{< fig "images/redirect.en.png" "" >}}

## Feedback

When enabling SRS, the `ENVELOPE FROM` and the `HEADER FROM`/`FROM` no longer match. If this allows to validate SPF, it will still not validate DMARC. The DMARC validation will depend only on the presence of a valid DKIM.

> The Noun Project

[^1]: [set up SPF at alwaysdata](e-mails/set-up-spf-dkim-dmarc#sender-policy-framework)

+++
url = "/emails/verifier-l-envoi-d-un-email/"
title = "How to check if an email has been sent"
hidden = true
layout = "howto"
tags = [ "email" ]
+++

You have access to the sending logs in the **Emails > History** menu.

{{< fig "images/history.png" "Latest Submissions List" >}}

- _[Score](e-mails/delivery#système-de-notation)_ : score given by alwaysdata antispam which determines whether an email is sent or not[^1] ;
- _Blocked_: if the email was blocked by the alwaysdata antispam. Not to be confused with a _bounce_[^2] that includes other reasons.

{{< fig "images/example.en.png" "Example of a shipment" >}}

- _Internal score_: score given by alwaysdata antispam;
- _Internal report_: details of the score given by the alwaysdata antispam. It takes into account the Rspamd score;
- _SPAM Score_: [Rspamd]score (https://www.rspamd.com/);
- _SPAM report_: details of the Rspamd score.

Only emails sent in the last _12 months_ are kept and, by default, only emails sent in the last _7 days_ are displayed.

[^1]: an email with a higher score to 3 will not be sent to shared servers. In Private Cloud, the default is 5 (changeable).

[^2]: this can block our antispam, a refusal by the recipient servers or a non-answer from them for several days, for example. The sender must then receive a _Mail delivery failed_ containing the reasons for the bounce.

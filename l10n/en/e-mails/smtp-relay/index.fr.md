+++
url = "/emails/relais-smtp/"
title = "SMTP Relay"
layout = "man"
hidden = true
tags = [ "email" ]
+++

The SMTP relay allows to use an external third-party server for sending emails. This may, for example, be useful for:

- do not touch the reputation of your alwaysdata server;
- take advantage of special services.

This option is available on [Private Cloud Plans](accounts/billing/private-cloud-prices) alwaysdata.

## Setting up

Go to the **SMTP > Settings** menu on your server and then enter the authentication information for the selected SMTP relay.

{{< fig "images/smtp-parameters.png" "" >}}

All emails in front of the server will leave the relay server.

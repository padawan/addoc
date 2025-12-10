+++
url = "/emails/collector-address/"
title = "Catch-all address"
layout = "faq"
hidden = true
tags = [ "email" ]
+++

To collect all messages sent to addresses in their non-existing domain (or more), a collector address (or [catch-all](https://fr.wikipedia.org/wiki/Catch-all)) can be created.

Representation: `*@example.org`

## Warning

- This may collect a large amount of spam. It is therefore advisable to activate anti-spam on this address;
- Error emails normally sent to non-existing addresses will no longer be sent. Be sure to alert any senders who believe the address is valid.

## Misc

- Due to its specifications, it is not possible to set up automatic response. This could otherwise cause waves of spam.

  - Nevertheless it is possible to use it for specific recipients via [Sieve scripts](e-mails/use-sieve-scripts) by adding these recipient addresses in the `vacation` statements:

  ```
  ["foo@example.org", "bar@example.org"] addresses
  ```

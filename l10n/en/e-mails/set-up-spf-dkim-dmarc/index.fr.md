+++
url = "/emails/configurer-spf-dkim-dmarc/"
title = "How to configure SPF/DKIM/DMARC"
layout = "howto"
hidden = true
tags = [ "email", "dns" ]
+++

Here are 3 ways to authenticate your emails and thereby reduce the misuse of emails (spam, phishing...).

## Sender Policy Framework

[SPF](https://fr.wikipedia.org/wiki/Sender_Policy_Framework) makes a DNS request of type `TXT` on the sender's domain \("_MAIL FROM_" in the message headers) to know the list of servers allowed to send emails and compare it to the sender's IP address.

{{< fig "images/globalcyberalliance-spf.en.png" "" >}}

### Parameters

| Mechanism |                                                                                                   |
| --------- | ------------------------------------------------------------------------------------------------- |
| ALL       | Default result                                                                                    |
| To        | A _IN A (or AAAA)_ record that can be resolved as a sender address             |
| IP4       | IPv4 Range                                                                                        |
| IP6       | IPv6 Range                                                                                        |
| MX        | A _Mail eXchanger_ record pointing to the address of the sender                                   |
| EXISTS    | Domain is resolved to any address                                                                 |
| INCLUDE   | An included issue passes the test                                                                 |
| PTR       | The domain of the IP address corresponds to the specific domain and it points to the IP in return |

| Qualifiers        |                                                                    |
| ----------------- | ------------------------------------------------------------------ |
| +                 | Favourite result                                                   |
| ?                 | Neutral result                                                     |
| ~ | Failed "_SOFTMAIL_" (email accepted but marked) |
| -                 | Total failure (email normally rejected)         |

| Modified                                                  |                                          |
| --------------------------------------------------------- | ---------------------------------------- |
| exp=some.example.org      | To get the reason for the results failed |
| redirect=some.example.org | To bind to another domain record         |

{{% notice warning %}}
This technology may have repercussions on email redirects: the sender server was not forced to be the mail server of the original email sender.
{{%/notice %}}

#### Alwaysdata

A SPF record is created by default, found in the **DNS Records** tab of the domain:

{{< fig "images/spf-record.png" "" >}}

- `include:_spf.alwaysdata.com` **explicitly allows our servers** to send emails;
- `~all` sends a failure leg "SOFTMAIL" for other upload servers.

If the domain does not use alwaysdata DNS servers, the DNS provider will need to add `include:_spf.alwaysdata.com` to the SPF record.

### Links

- [RFC 7208](https://tools.ietf.org/html/rfc7208)
- [RFC 7372 - point 3.2](https://tools.ietf.org/html/rfc7372)
- [RFC 4408](https://tools.ietf.org/html/rfc4408)

## DomainKeys Identified Mail

[DKIM](https://fr.wikipedia.org/wiki/DomainKeys_Identified_Mail) allows to authenticate the domain name by adding a signature to all outgoing emails. Concrete it works with two keys:

- a private key that is known - and kept secret - of mail servers sending domain addresses;
- a public key that matches a DNS record of type `TXT`.

{{< fig "images/globalcyberalliance-dkim.en.png" "" >}}

### Alwaysdata

A keypair is created by default, whose public key (the `TXT` record) is found in the **DNS Records** tab of the domain:

{{< fig "images/dkim-record.png" "" >}}

If the domain does not use alwaysdata DNS servers, this record must be copied to the DNS provider.

> Il est possible d'en générer d'autres dans **Domaines > Détails de [example.org] - 🔎 > Configuration**.

### Links

- [RFC 6376](https://tools.ietf.org/html/rfc6376)
- [RFC 7372 - point 3.1](https://tools.ietf.org/html/rfc7372)

## Domain-based Message Authentication, Reporting and Conformance

[DMARC](https://fr.wikipedia.org/wiki/DMARC) is a protocol that standardizes authentication by telling recipients what to do in case one of the authentication methods fails. It will check that:

- domain matches DKIM keypair (_d=_) field;
- sending server is specified in SPF domain record (_MAIL FROM_);
- domain is in the _FROM_ field of the email.

{{< fig "images/globalcyberalliance-dmarc.en.png" "" >}}

{{% notice info %}}
To use DMARC, DKIM and SPF must be implemented already.
{{%/notice %}}

### Parameters

| Variables |                                                                                                                                   |
| --------- | --------------------------------------------------------------------------------------------------------------------------------- |
| v         | Protocol version: `v=DMARC1` (required)                                                        |
| pct       | Percentage of messages filtered (default: 100)                                                 |
| adkim     | DKIM Coherence                                                                                                                    |
|           | `s` = strict mode - DKIM signature domain must match exactly the _FROM_                                                           |
|           | `r` = relax mode (default)                                                                                     |
| aspf      | Coherence with SPF (`s or `r\`)                                                                                |
| p         | Procedures on failure - main domain (required)                                                                 |
|           | `none` = deliver the email normally                                                                                               |
|           | `quarantine` = treat email as suspicious (spam score, flag...) |
|           | `reject` = rejects email                                                                                                          |
| sp        | Proceed on failure - subdomain (`none`, `quarantine` or `reject`)                                              |
| ruf       | Recipient of detailed failure reports                                                                                             |
| fo        | Conditions for sending a detailed report                                                                                          |
|           | `1` = DKIM and/or SPF failure                                                                                                     |
|           | `d` = DKIM failure                                                                                                                |
|           | `s` = SPF failure                                                                                                                 |
|           | `0`= DKIM and SPF failed (default)                                                                             |
| rua       | Accepted Chess Reports Recipients                                                                                                 |

To set it up, a DNS record of type `TXT` must be created. At alwaysdata you will find it in the **DNS Records** tab of the domain:

{{< fig "images/dmarc-record.png" "" >}}

### Links

- [Official Site](https://dmarc.org/)
- [RFC 7489](https://tools.ietf.org/html/rfc7489)

-----

Explanatory schemas taken from [Global Cyber Alliance](https://dmarc.globalcyberalliance.org/)


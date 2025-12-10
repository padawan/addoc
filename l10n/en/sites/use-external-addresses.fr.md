+++
url = "/sites/user-external-addresses/"
title = "How to use external addresses"
layout = "howto"
hidden = true
tags = [ "dns", "http", "site" ]
+++

To use your own addresses without [managing your domain](domains/add-an-external-domain) at alwaysdata, you must:

1. at the domain DNS provider, create [DNS records](https://fr.wikipedia.org/wiki/Liste_des_enregistrements_DNS) pointing to your alwaysdata account;

   - The server an account is on can change. It is therefore preferred to use records of type _CNAME_ with value `<compte>. lwaysdata.net` (`<compte>` with account name) rather than _A_/_AAAA_records.

{{% notice tip %}}
The _CNAME_ is not available for the empty subdomain, will then be used the types _A_/_AAAA_ or _ALIAS_ with the IP address of the HTTP server (found in the **Forward** section of the alwaysdata administration interface).
{{%/notice %}}

2. on the alwaysdata admin interface, [declare addresses](sites/add-a-site) in **Web > Sites**.

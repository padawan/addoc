+++
url = "/security/ssl-tls/priorite-de-renvoi-des-certificats-ssl"
title = "What SSL certificate is returned by default?"
layout = "faq"
hidden = true
tags = [ "https", "ssl" ]
+++

Grade to [SNI](https://datatracker.ietf.org/doc/html/rfc6066#section-3), the server will return in order of priority, if specified in **Advanced> SSL Certificates** and is not expired:

- Your certificate was manually added matching the host name.
- Your wildcard certificate manually added corresponding to the domain name.
- The [Let's Encrypt self-managed certificate](security/ssl-tls/lets-encrypt#automatically-generated-certificates) corresponding to the host name.
- The default certificate of the server.

If you want to return a certificate with lower priority, you can attach the latter directly to the subdomain, **it will take precedence over the others**.

Configuring the priority of a certificate is _only_ possible for the certificates you have added. This is not an option available for Let's Encrypt certificates.

To force a certificate go to the SSL certificate configuration - menu **Advanced > SSL Certificates** or to the subdomain configuration - menu **Domains > [domaine] details - ⚙️ > Subdomains**.

{{% notice warning %}}
A certificate expired, if it is attached to a subdomain, will still be returned by the server.
{{%/notice %}}

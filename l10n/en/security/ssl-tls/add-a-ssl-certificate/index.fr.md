+++
url = "/security/ssl-tls/ajouter-certificat-ssl"
title = "How to add an SSL certificate to its site"
linkTitle = "Add SSL Certificate"
layout = "howto"
weight = 10
tags = [ "https", "security", "ssl" ]
+++

{{< fig "images/admin-panel_ssl-list.png" "Admin interface: SSL Certificates menu" >}}
{{< fig "images/admin-panel_ssl-add.en.png" "Admin interface: add certificate" >}}

Private key, certificate and certificates must be in PEM format.

You can add certificates for a specific address, [SAN]certificates (https://en.wikipedia.org/wiki/Subject_Alternative_Name) (multi-domain) or [wildcard]certificates (https://en.wikipedia.org/wiki/Wildcard_certificate).

If you do not have an SSL certificate, you can use our [Let's Encrypt certificates](security/ssl-tls/lets-encrypt) or buy one from an SSL certificate provider by giving it the [previously created CSR](security/ssl-tls/csr).

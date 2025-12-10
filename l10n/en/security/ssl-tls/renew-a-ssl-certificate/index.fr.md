+++
url = "/security/ssl-tls/renouveler-un-certificat-ssl"
title = "How to renew an SSL certificate"
layout = "howto"
hidden = true
tags = [ "https", "security", "ssl" ]
+++

When you renew the SSL certificate at your provider, it must deliver you a file containing the new certificate.

On your alwaysdata interface - tab **Advanced> SSL Certificates** - then change the current certificate.

{{< fig "images/ssl-certificates_list.png" "" >}}

Change the **Certificate** field to put the contents of the file given by your SSL certificate provider.

{{< fig "images/modify-certificate.png" "" >}}

The certificate is now updated and its new expiration date will be displayed.

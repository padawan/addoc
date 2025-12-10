+++
url = "/security/ssl-tls/"
title = "SSL/TLS"
weight = 20
archetype = "chapter"
tags = [ "https", "security", "ssl" ]
+++

All services (HTTP, but also remote access, databases, emails...) are secured by an SSL/TLS layer.

- [Let's Encrypt Certificates](lets-encrypt)
- [Redirect HTTP to HTTPS](redirect-http-to-https)
- [Manage CSR](csr)
- [Add SSL Certificate](add-a-ssl-certificate)
- [Renew SSL Certificate](renew-a-ssl-certificate)
- [Certificate Priority](certificates-priorities)

* [API](https://api.alwaysdata.com/v1/ssl/doc/)
* [Configure TLS](configure-tls)
* [Implement HSTS](hsts)

- Check the certificate returned and setting up a host name: [SSL Labs](https://www.ssllabs.com), [SSL Tools](https://ssl-tools.net/) or [Security Headers](https://securityheaders.com).
- Find mixed content [^1] from its website: [Why no Padlock](https://www.whynopadlock.com/).

[^1]: Browsers return the "Mixed content" error when a website uses HTTPS but images, blank or scripts/styles are returned over HTTP.

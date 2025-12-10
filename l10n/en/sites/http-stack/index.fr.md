+++
url = "/sites/stack-http/"
title = "HTTP Stack"
hidden = true
layout = "man"
tags = [ "http", "site" ]
+++

A front-end reverse-proxy is installed on all our servers. This listens for incoming HTTP requests and:

- launches HTTP servers and [définis]programs (sites/add-a-site) to serve your data;
- returns the voucher [SSL certificate](security/ssl-tls/certificates-priorities);
- log HTTP requests. These logs are available through the [$HOME/admin/logs\`](remote-access/admin-directory#logs).

It also manages the [web application firewall (WAF)](sites/waf) and the [HTTP cache] (http-cache) that can be enabled in **Web > Sites**.

{{< fig "images/http-stack.en.png" "Alwaysdata reverse-proxy operation" >}}

We add to _headers_:

- `X-Forwarded-Proto`, which is http or https depending on whether the connection is made in HTTP or HTTPS. Thus the reverse proxy access to HTTP web servers whether the browser connection is HTTP or HTTPS;
- `X-Real-IP`, which takes the value of the user's IP address.

---

The Noun Project

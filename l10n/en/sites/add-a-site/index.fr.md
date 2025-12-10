+++
url = "/sites/add-a-site/"
title = "How to add a site"
linkTitle = "Create a site"
layout = "howto"
weight = 1
tags = [ "http", "site" ]
+++

{{< fig "images/admin-panel_sites-list.png" "Admin interface: list of sites" >}}

{{% notice tip %}}
If you leave from zeÉro you can enjoy our [marketplace](marketplace) by going to **Web > Sites > Install an App**.
{{%/notice %}}

## Addresses

Adding all addresses to this menu is an **impediment** for them to be accessible as sites:

- for example, to access a site on _www\.example.org_ and _example.org_ both addresses must be added;
- setting its domain in the **Domains** menu is not enough either. Meme for a domain using our [DNS servers](domains#gestion-dns).

Moreover, if the domain does not use our DNS servers, you will need to [create DNS records](sites/use-external-addresses) at the DNS provider.

{{< fig "images/admin-panel_add-site-general.png" "General" >}}

{{% notice note %}}
Adding the site will not create the _root directory_, it must be created by [remote access](remote-access).
{{%/notice %}}

To create a catch-all type `*.example.org`.

## Setup

Specific to each site type:

- [PHP](languages/php);
- [Python WSGI](languages/python);
- [Ruby Rack](languages/ruby);
- Ruby on Rails <= 2.x;
- [Node.js](languages/nodejs);
- [Elixir](languages/elixir);
- [Deno](languages/deno);
- [.NET](languages/dotnet);
- [Java](languages/java);
- [Redirection](sites/redirect);
- Reverse proxy: Set up a reverse proxy to a URL;
- [Static Files](sites/static-files): to manage static sites or files;
- [Custom Apache](sites/apache-custom): to fully configure its Apache server;
- [User program](sites/user-program) : to run any web server.

PHP sites, static files, and custom Apache sites are served by [Apache](https://httpd.apache.org/). Python WSGI, Ruby Rack and Ruby on Rails <= 2.x use [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/).

## SSL

{{< fig "images/admin-panel_add-site-ssl.png" "Redirect HTTP requests to HTTPS" >}}
See [SSL](security/ssl-tls/redirect-http-to-https).

## WAF

{{< fig "images/admin-panel_add-site-waf.en.png" "Configure web application firewall" >}}
See [WAF](sites/waf).

## Cache

{{< fig "images/admin-panel_add-site-cache.png" "Set up HTTP Cache" >}}
See [Cache](sites/http-cache).

## Logs

{{< fig "images/admin-panel_add-site-logs.en.png" "Customize HTTP logs" >}}
See [Logs](sites/formatting-http-logs).

## Advanced

{{< fig "images/admin-panel_add-site-advanced.en.png" "" >}}

> [idle time](sites/misc#temps-dinactivité)

---

HTTP logs are available in the `$HOME/admin/logs/http/` directory. The _sites_ logs containing launches, stops, and malfunctions of upstream web servers are available in `$HOME/admin/logs/sites/`. An excerpt of these logs (as well as the Apache and uWSGI logs) is presented in the alwaysdata administration interface (**Logs** - 📄).

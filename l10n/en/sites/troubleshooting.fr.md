+++
url = "/sites/frequent-issues/"
title = "Websites - Problems"
layout = "faq"
weight = 90
tags = [ "troubleshooting", "http", "site" ]
+++

## Login

External service to check availability: [Where's It Up?](https://wheresitup.com/)

- Connection to upstream refused, Connection to upstream skipped, Upstream not ready, Cannot parse upstream response](sites/connection-to-upstream)
- [PHP](languages/php/troubleshooting)

### This site could not be reached / server DNS address could not be found

- Check if the domain exists, is not expired or blocked by the[ICANN](https://www.icann.org/fr) via a `whois`[^1] ;
- Check the [DNS solution](https://www.dnswatch.info/) of the address.

Adding the domain to **Domains** is not enough to create a website. Adding addresses to **Web > Sites** is required.

### 403 Forbidden

For sites using [Apache](sites/configure-apache), a file named `index.html` or `index.php` should be searched for the home page. Rename your file or use the [DirectoryIndex]directive (https://httpd.apache.org/docs/2.4/fr/mod/mod_dir.html#directoryindex) in a `.htaccess`.

### 500 Errors

These errors can be returned by the web server (e.g. Apache), the language used, or the application itself. Setting up debug logs allows you to have more information to fix.

### White Page

A blank page with no message or error code means an application problem: the code returned from HTTP logs is _200_, indicating that the request reaches the application. Setting up debug logs allows you to have more information to fix.

## Apache Logs

Logs are available in the `$HOME/logs/apache` directory.

### Broken pipe / Connection reset by peer

```txt
Broken pipe: [X.X.X:0] mod_fcgid: ap_pass_brigade failed in handle_request_ipc function
(104)Connection reset by peer: [X.X.X.X:0] mod_fcgid: ap_pass_brigade failed in handle_request_ipc function
```

The connection was broken by the client. For example, because the visitor closed his tab while the page was not fully loaded. **This is not abnormal.**

### Premature script headers

```txt
Premature end of script headers: index.php, referer: https://example.org
```

The _server_ suddenly stopped and Apache returned an error 500. **This should not happen in normal situation.** This can be due to many reasons (PHP bug, application bug, kernel kill PHP process, etc.).

You have to parse all the logs at your disposal to find the cause: application logs, PHP logs...

[^1]: More information about [whois](https://fr.wikipedia.org/wiki/Whois)

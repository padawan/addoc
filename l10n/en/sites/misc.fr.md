+++
url = "/sites/diverse/"
title = "Various questions"
layout = "faq"
hidden = true
tags = [ "http", "site" ]
+++

## Default HTTP Site

This option, [Private Clouds](accounts/billing/private-cloud-prices) and settings in the **HTTP** menu on the server, directive provides a site to redirect incoming requests to the server whose address is not defined in the alwaysdata administration interface. This will override the "_Site not found_" returned by default.

This is useful when addresses point to the DNS level on the server but are not filled in **Web > Sites**. This may, for example, in the case of a site with a number of addresses - which you do not want all listed in **Sites** - or a forgotten.

## Inactivity time

Settings in the **Web > Sites > Edit [site] - ⚙️ > Advance**. This allows you to choose the hardness after which the system stops the application; if there is no longer any activity. Once an HTTP request is executed, the application will be restarted.

For an application to never be stopped, set it as `0`.

There is, however, _no guarantee_ that an application will never be stopped and it can be stopped at any time. If _necessary_ a web app is running 24/7 create an [service](services) and a [Redirect proxy"](sites/redirect) for its web access.

## Useful commands

- Know which IPs made the most requests at a date:

```
cut -d' -f2 $HOME/admin/logs/http/[année]/[fichier].log | sort | uniq -c | sort -rn | head
```

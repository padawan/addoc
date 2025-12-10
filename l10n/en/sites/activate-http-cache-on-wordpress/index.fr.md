+++
url = "/sites/enable-le-cache-http-sur-wordpress"
title = "Enable HTTP Cache on WordPress"
hidden = true
layout = "howto"
tags = [ "cache", "http", "wordpress" ]
+++

1. Install the [WP Super Cache](https://wordpress.org/plugins/wp-super-cache/) plugin in the WordPress admin interface. Enable it, then cache in its settings:

{{< fig "images/activate-wp-cache.png" "" >}}

Several parameters can later be modified.

2. Enable [HTTP cache](sites/http-cache) on the website in **Web > Sites > Edit [site] - ⚙️ > Cache**.

3. Check if cache is active:

- Once on the WordPress homepage, open your browser developer panel, menu _Network_/_Network_. Search the `Age` header.

{{< fig "images/result.en.png" "" >}}

- or using `curl -I`:

```sh
$ curl -I https://httpcache.alwaysdata. and
HTTP/2 200 
date: Wed, 01 Dec 2021 16:04:55 GMT
server: Apache
vary: Accept-Encoding, ookie

cache-control: max-age=3, must-revalidate

content-type: text/html; charset=UTF-8
via: 2. alproxy
```

If your site returns the `cache-control: max-age=0`, it is not hidden.

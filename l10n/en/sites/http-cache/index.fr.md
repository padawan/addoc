+++
url = "/sites/cache-http/"
title = "HTTP Cache"
weight = 50
layout = "man"
tags = [ "cache", "http", "site" ]
+++

The HTTP cache stores web documents template(examples: HTML pages, CSS documents), images) to dimify the latency induced by the server when it has to serve a page and/or reduce its workload.

- [Enable HTTP Cache on WordPress](sites/activate-http-cache-on-wordpress)

## Concept

When a user tries to access a page, the corresponding web server will manage a page and send it to the network. The cache then intercepts the response to store it in its local memory before serving it to the user.

{{< fig "http-cache_part-1.en.png" "Caching a source when requesting" >}}

When a request for the same page is issued by the same or another user, the cache will render it as it holds a copy of the requested source. The web server will no longer be interrogested.

{{< fig "http-cache_part-2.en.png" "Retrieving a previously cached source" >}}

The characteristics of the standard are exposed in the [RFC 7234](https://tools.ietf.org/html/rfc7234).

## Use HTTP Cache

### 1. Make sure your app geocaches the cache

To enable the cache to query the upstream for the purpose of knowing if the target resource has not been modified, the application **must** provide the `Etag` and/or `Last-Modified` header.

A response cannot **NOT** be hidden if:

- the **`Vary`** header is `*`;
- the **`Content-Type`** header is not present;
- the header **`Content-Type`** is not one of the values: `text/html`, `text/xml`, `text/plain`, `application/xml`, `application/html+xml`, `application/rss+xml`, `application/rdf+xml`, `application/atom+xml`, `text/css`, `text/javascript`;
- the **`Cache-Control`** header is one of the values: `private`, `no-store`, `no-cache`, `no-transform`;
- **Set-Cookie\`** header is available;
- the **`Authorization`** header exists but **`Cache-Control`** has none of the following values: `public`, `must-revalidate`, `proxy-revalidate`, `s-maxage`;
- **HTTP_** status code is not one of the following: 200, 203, 204, 206, 300, 301, 404, 405, 410, 414, 501.

### 2. Enable HTTP Cache

Go to **Web > Sites > Edit [site] - ⚙️ > Cache**.

{{< fig "admin-panel_add-site-cache.png" "" >}}

### Using `PURGE`

`PURGE` can be executed in three different ways at alwaysdata:

1. using the full URL of the resource (e.g. `https://test.alwaysdata.net/foo/bar`). This will remove the related cache intern and its variations (managed by the `Vary` header);
2. by adding the `X-Cache-Purge-Match: wildcard` and adding a wildcard to your URL (e.g. `https://test.alwaysdata.net/*`). This will remove all entries matching the URL pattern;
3. by adding the `X-Cache-Purge-Match: startswith` and adding a partial path to your URL (e.g. `https://test.alwaysdata.net/foo`). This will remove all entries matching the URL pattern (and thus `https://test.alwaysdata.net/foo/bar`).

{{% notice note %}}
Although the HTTP cache works in the vast majority of cases, you can also [run Varnish](sites/user-program) on your alwaysdata account.
{{%/notice %}}

> The Noun Project

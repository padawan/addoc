+++
url = "/security/ssl-tls/hsts/"
title = "How to simplify HSTS"
layout = "howto"
hidden = true
tags = [ "https", "security", "ssl" ]
+++

The [HTTP Strict Transport Security](https://fr.wikipedia.org/wiki/HTTP_Strict_Transport_Security) policy allows users to be protected by declaring to browsers that they must interact with the web server using a secure connection.

Setting it up requires adding `headers`.

## Apache

- Add it for all Apache sites in the account via global directives (menu **Web > Configuration > Apache**):

```txt
Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains"
```

- Or for each site by adding at the beginning of the created `.htaccess` to the root of the sites:

```txt
<IfModule mod_headers.c>

Header always set Strict-Transport-Security "max-age=31536000; includeSubDomains"

</IfModule>
```

## uWSGI

Add to uWSGI additional settings (**Web menu > Sites > Edit [site] - ⚙️ > Advanced configuration**):

```txt
plugins = router_redirect
route-if-not = equal:${HTTPS};on redirect-permanent:https://${HTTP_HOST}${REQUEST_URI}
route-if = equal:${HTTPS};on addheader:Strict-Transport-Security: max-age=31536000
```

- [Documentation](https://uwsgi-docs.readthedocs.io/en/latest/Snippets.html)

## Node.js

To put any other controller first:

```txt
app.use(req, res, next) {
  if (req.secure) {
    res.setHeader('Strict-Transport-Security', 'max-age=63072000; includeSubDomains') // 2 years
  }
  next()
})
```

Another method with the `helmet` NPM package:

```txt
var helmet = require('helmet')
    ... 
    app.use(helmet.hsts({
          maxAge: 31536000000,
          includeSubdomains: true,
          force: true
    }));
```

## Guidelines

- `max-age` defines the period of application of a HSTS policy by browsers (31536000 = for a year);
- `includeSubDomains` allows HSTS to be applied both to the domain and to its subdomains;
- `preload` allows adding the site to preloaded HSTS lists.

`max-age` is mandatory unlike others.

---

- [RFC 6797](https://tools.ietf.org/html/rfc6797)
- Check its HSTS configuration via [HSTS preload](https://hstspreload.org/)


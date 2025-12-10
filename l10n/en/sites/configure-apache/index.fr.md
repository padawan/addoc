+++
url = "/sites/configurer-apache/"
title = "How to change its Apache server configuration"
linkTitle = "Apache Configuration"
layout = "howto"
weight = 10
tags = [ "apache", "http", "site" ]
+++

{{< fig "images/admin-panel_apache.png" "Admin interface: configuring Apache" >}}

All changes made in the _Global Apache Guidelines_ field will run in the `$HOME/admin/config/apache/sites.conf` file. Apache error logs are available in the `$HOME/admin/logs/apache/apache.log` file. An excerpt of these logs is present in the alwaysdata administration interface (Logs - 📄).

Apache serves PHP sites, static files, and custom Apache sites.

- [Apache documentation 2.4](http://httpd.apache.org/docs/2.4/fr/)
- [.htaccess file](sites/htaccess-file)

## Install a module

Once the `.so` file compiles and adds to your [file space](remote-access), set this line to the global directives:

```
LoadModule <MODULE> $HOME/path/to/module.so
```

- [GeoIP](guides/geoip)

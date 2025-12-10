+++
url = "/sites/static-files/"
title = "How to use static files type"
linkTitle = "Static Files"
layout = "howto"
weight = 15
tags = [ "apache", "http", "site" ]
+++

Whether it is to manage a static site, like an HTML site, or to serve media from a site using uWSGI, you can use the static files type.

{{< fig "images/admin-panel_sites-list.png" "Admin interface: list of sites" >}}

- Name: Used for display in the alwaysdata admin interface purely informative;
- Addresses: the addresses to join your site (`*.example.org` for _catch-all_);

{{< fig "images/admin-panel_add-site-general.png" "Add site: manager" >}}

- Type: Static files;
- Root directory: directory in which your application is placed.

{{< fig "images/admin-panel_static-files.en.png" "Add Site: Static Files" >}}

## Error messages

### 403 Forbidden

By default, the HTTP server will search for a file named `index.html` for the home page. Rename your file or use the [DirectoryIndex]directive (https://httpd.apache.org/docs/2.4/fr/mod/mod_dir.html#directoryindex) in a `.htaccess`.

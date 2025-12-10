+++
url = "/sites/redirection/"
title = "How to redirect HTTP addresses"
linkTitle = "Address Redirect"
layout = "howto"
weight = 5
tags = [ "http", "redirect", "site" ]
+++

Go to the **Web > Sites > Add Site** menu.

{{< fig "images/admin-panel_sites-list.png" "Admin interface: list of sites" >}}

- Name: Used for display in the alwaysdata admin interface purely informative;
- Addresses: the addresses to join your site (`*.example.org` for _catch-all_);

{{< fig "images/admin-panel_add-site-general.png" "Add site: manager" >}}

- Type: Redirect;
- Destination URL: address to which the redirect will be made;
- Redirect type:
  - Permanent (HTTP code `301`) : for normal use, redirect a visitor from an address A to an address B. Search engines that update their index with the new landing page;
  - temporary (HTTP code `302`): Generally used when maintaining a site. Search engines keep the start page in their index;
- Add the request path to the destination URL.

{{< fig "images/admin-panel_redirect.en.png" "Add Site: Redirect" >}}

## Redirect via Apache

For PHP sites, static files, and custom Apache sites, you can also use a `.htaccess` file and the [Redirect]directive (https://httpd.apache.org/docs/2.4/fr/mod/mod_alias.html#redirect).

## Redirect via uWSGI

For sites like Python WSGI, Ruby Rack and Ruby on Rails <= 2. , you can also use the [InternalRouting]method (https://uwsgi-docs.readthedocs.io/en/latest/InternalRouting.html) and its `router-redirect` plugin in the advanced site configuration.

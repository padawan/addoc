+++
url = "/sites/apache-customize/"
title = "How to use custom Apache type"
layout = "howto"
hidden = true
tags = [ "apache", "http", "site" ]
+++

The custom Apache type allows to run sites served by the Apache server but not using PHP or HTML.

{{% notice warning %}}
If you just want to add global directives to Apache change its [configuration](sites/configure-apache) in **Web > Configuration > Apache**.
{{%/notice %}}

{{< fig "images/admin-panel_sites-list.png" "Admin interface: list of sites" >}}

- Name: Used for display in the alwaysdata admin interface purely informative;
- Addresses: the addresses to join your site (`*.example.org` for _catch-all_);

{{< fig "images/admin-panel_add-site-general.png" "Add site: manager" >}}

- Type: Custom Apache
- Global Guidelines: Global guidelines for all sites served by Apache;
- Virtual host guidelines: Apache directives for the relevant site.

{{< fig "images/admin-panel_apache-custom.png" "Add a site: custom Apache" >}}

All changes will occur in the `$HOME/admin/config/apache/sites.conf` file. Apache error logs are available in `$HOME/admin/logs/apache/apache.log`.

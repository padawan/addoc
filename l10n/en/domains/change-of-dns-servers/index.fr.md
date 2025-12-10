+++
url = "/domains/changer-de-serveurs-dns/"
title = "How to change DNS servers"
linkTitle = "Change DNS servers"
layout = "howto"
weight = 21
tags = [ "dns", "domain" ]
+++

The [DNS servers](https://fr.wikipedia.org/wiki/Domain_Name_System) define which servers to contact for each service. They are therefore defined at the registrar - the provider of the administrative management of the domain.

1. Ask your new DNS service provider;
2. In your admin interface, go to **Domains > Details** of the domain concerned **> Modify** its DNS servers;
   {{< fig "images/admin-panel_domain-details. r.png" "Admin interface: Domain details" >}}
3. Specify the addresses of your new DNS servers.  
   {{< fig "images/admin-panel_change-dns.en.png" "Admin interface: Change DNS servers" >}}

{{% notice note %}}
When DNS server fields are empty, the domain uses alwaysdata DNS servers.
{{%/notice %}}

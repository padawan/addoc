+++
url = "/domaines/ajouter-un-domaine-externne/"
title = "How to add an external domain"
linkTitle = "Add External Domain"
layout = "howto"
weight = 5
tags = [ "domain" ]
+++

It is free to transmit _technical_ domain management without touching _administrative_ (its registrar). If you want to pass all the management at alwaysdata, go through a [domain transfer] (domains/transfer-a-domain).

Here we want to add the domain and **change DNS servers** to the registrar to put `dns1.alwaysdata.com` and `dns2.alwaysdata.com`.

1. In your admin interface, go to **Domains > Add Domain**;
   {{< fig "images/admin-panel_domain-list.en.png" "Admin interface: list of domains" >}}
2. Enter the domain names you want to add;
   {{< fig "images/admin-panel_add-domain-1. ng" "Admin interface: step 1" >}}
   {{% notice info %}}
   Enter only the domain, without the subdomain. For example: example.org and not www.example\\.org.   
{{%/notice %}}
3. Choose to **manage** it.  
   {{< fig "images/admin-panel_add-domain-2.en.png" "Administration interface: Step 2" >}}

This will add the domain as _external domain_ in the list.

{{< fig "images/admin-panel_domain-list2.en.png" "Admin interface: External Domain" >}}

You can then create [email addresses](e-mails/create-an-e-mail-address), [web sites](sites/add-a-site) and manage [DNS records](domains/add-dns).

{{% notice warning %}}
If some DNS records need to be kept - for example do not change email providers - you will need to prepare the [DNS area](domains/add-dns) before changing DNS servers.
{{%/notice %}}

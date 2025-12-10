+++
url = "/domaines/add-un-registrment-srv/"
title = "How to add a SRV record"
layout = "howto"
hidden = true
tags = [ "dns", "domain" ]
+++

A [SRV record](https://fr.wikipedia.org/wiki/Enregistrement_de_service) defines the location of specific services.

1. Go to **Domains > [example.org] Details - 🔎 > DNS Records**;
   {{< fig "images/admin-panel_dns-record-list.png" "Admin interface: DNS records list" >}}

2. Choose **Add DNS record**;

3. Fill in the form.  
   {{< fig "images/admin-panel_add-srv.fr.png" "Admin interface: add SRV record" >}}

{{% notice warning %}}
Do not put the root in **Host Name**.
For example, by entering `www.example.org` in this box, you will create a record for `www.example.org.example.org`.
{{%/notice %}}

## Some examples

- Automatically configure a mail client with `_autodiscover._tcp`:
    ```
    » Host name: _autodiscover._tcp
    » Value: 0 443 address.server.mail
    » Priority: 1
    » TTL: 300
    ```

- Use Lync (formerly Skype) with `_sip._tls` and `_sipfederationtls._tcp`:
    ```
    » Hostname: _sip._tls
    » Value: 1 443 sipdir.online.lync.com
    » Priority: 100
    » TTL: 3600
    ```
    ```
    » Host name: _sipfederationtls._tcp
    » Value: 1 443 sipfed.online.lync.com
    » Priority: 100
    » TTL : 3600
    ```

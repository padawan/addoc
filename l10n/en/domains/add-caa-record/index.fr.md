+++
url = "/domains/add-a-registrment-caa/"
title = "How to add a CAA record"
layout = "howto"
hidden = true
tags = [ "dns", "domain" ]
+++

A [CAA registration](https://fr.wikipedia.org/wiki/DNS_Certification_Authority_Authorization) lists the certified certifications authority for a domain. Any certification authority not part of the issuers authorized by the CAA registration of a domain will not be authorized to issue certificates for this domain or any subdomain.

1. Go to **Domains > [example.org] Details - 🔎 > DNS Records**;
   {{< fig "images/admin-panel_dns-record-list.png" "Admin interface: DNS records list" >}}

2. Choose **Add DNS record**;

3. Fill in the form.  
   {{< fig "images/admin-panel_add-caa.en.png" "Administration interface: add CAA record" >}}

{{% notice warning %}}
Do not put the root in **Host Name**.
For example, by entering `www.example.org` in this box, you will create a record for `www.example.org.example.org`.
{{%/notice %}}

Three labels are defined:

- `issue` that allows an authority;
- `issuewild` that allows an authority for wildcard certificates;
- `iodef` that reports a URL that can be contacted by certification authorities in case of problems.

{{% notice info %}}
[Let's Encrypt certificates](security/ssl-tls/lets-encrypt) is managed for any HTTP address hosted on our servers. They must therefore be part of the valid authority.
{{%/notice %}}

## Some examples

- Let's Encrypt Authorization:

    ```
    » Host name: [leave empty]
    » Value: 0 issue "letsencrypt.org"
    » TTL: 300
    ```

----

- [RFC 6844](https://tools.ietf.org/html/rfc6844)

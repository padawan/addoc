+++
url = "/domains/transferer-un-domain/"
title = "How to transmit a domain"
linkTitle = "Transfers a domain"
layout = "howto"
weight = 2
tags = [ "domain" ]
+++

OPERation [payante](https://www.alwaysdata.com/fr/domaines/#main), it allows to transmit the _administrative_ management of its domain to alwaysdata.

{{% notice warning %}}
If you want to transfer the domain to another alwaysdata client, go through a [domain move](domains/move-a-domain).
{{%/notice %}}

## Preparation upstream

Before starting the project the owner must:

- remove transfer protection;
- make sure the property information is correct and visible in the `whois` [^1] ;
- get authorization code;
- Retrieve a backup of its data (including emails).

A transfer cannot take place within 60 days of its creation, or a previous transfer.

{{% notice tip %}}
The transfer of [technical management](domains/add-an-external-domain) can be done before to avoid being affected by the time taken by the administrative transfer.
{{%/notice %}}

## Launching transfer

1. In your admin interface, go to **Domains > Add Domain**;

       {{< fig "images/admin-panel_domain-list.en.png" "Admin interface: list of domains" >}}

   If the domain has already been [ajouté](domains/add-an-external-domain) to your alwaysdata interface you can transmit it via **Domains > Details** of the relevant domain **> Transaction**.

       {{< fig "images/admin-panel_transfer-domain.png" "Administration interface: Transfer of a domain to management" >}}

2. Enter the domain names you wish to purchase;

       {{< fig "images/admin-panel_add-domain-1.en.png" "Admin interface: Step 1" >}}

{{% notice info %}}
Enter only the domain, without the subdomain.
For example: `example.org` and not `www.example.org`.
{{%/notice %}}

3. Choose to **transmitter**;
   {{< fig "images/admin-panel_add-domain-2.en.png" "Administration interface: Step 2" >}}

4. - Specify the _authorization code_ if the extension requests it;
   - Choose whether or not to use our DNS servers: this involves transferring the technical domain management to alwaysdata;
   - And enter proprietary contact information. This information depends on the extension taken.
       {{< fig "images/admin-panel_add-domain-3.en.png" "Admin interface: Step 3" >}}

{{% notice warning %}}
A validation email is sent for a number of extensions. Without validation, the transfer is aborted.
{{%/notice %}}

{{% notice note %}}
A transfer takes an average of 6 to 8 days, this can be accessed by contacting your current provider.
{{%/notice %}}

### Special Cases

the IPS Tag requested by [Nominet](https://registrars.nominet.uk/) - the register of `.uk` - is **GANDI**.

## Realm Preparation

During this time, the domain will be added to your administration interface as _External Domain_ with an ongoing operation. You can prepare our servers by:

- updating your [DNS records](domains/add-dns) if you use other servers for certain services;
- creating [email addresses](e-mails/create-an-e-mail-address).

Regarding the website, several choices are possible:

- add addresses before they point to our servers. In this case, there may be a timeframe for managing [SSL Let's Encrypt Certificates](security/ssl-tls/lets-encrypt);
- prepare the site on another address and wait for the last moment to add the addresses to the site. It can then pass a time or the site is no longer accessible.

---

## Links

- [Transfers: error code](/domains/troubleshooting#transfert)

[^1]: More information about [whois](https://fr.wikipedia.org/wiki/Whois)

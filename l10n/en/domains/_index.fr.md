+++
url = "/domains/"
title = "Domains"
pre = "<i class='fas fa-fw fa-server'></i> "
weight = 16
archetype = "chapter"
tags = [ "dns", "domain" ]
+++

Domains are managed in the **Domains** tab of your admin interface. [Achetez](buy-a-domain), [transférez](transfer-a-domain) or [add in management](add-an-external-domain) your domain. Reseller [GANDI](https://www.gandi.net/fr), we rely on their expertise to offer you as many extensions as possible. [Contactez-nous](https://admin.alwaysdata.com/support/add/) if the desired extension is not offered by default.

{{% notice note %}}
As a GANDI reseller you can receive emails from us of theirs and [registres](https://fr.wikipedia.org/wiki/Registre_de_noms_de_domaine) handling domain extensions taken.
{{%/notice %}}

## Resources

- [Prix](https://www.alwaysdata.com/fr/domaines/#main)
- [Buy a domain](buy-a-domain)
- [Transfere Domain](transfer-a-domain)
- [Add External Domain](add-an-external-domain)

* [Renew a domain](renew-a-domain)
* [Boundary dates](deadlines)
* [Change property](change-of-owner)
* [Update Domain Owner Information](update-owner-details)
* [Destroy a domain](wipe-a-domain)
* [Set up DNSSEC](dnssec)

- [Move a domain](move-a-domain)
- [Delegate a subdomain](delegate-a-subdomain)
- [Outgoing transfer](outgoing-transfer)

* [API - Domain](https://api.alwaysdata.com/v1/domain/doc/)
* [Freight issues](./troubleshooting)

{{% notice warning %}}
officially invalid (after [IDNA2008](http://unicode.org/faq/idn.html)), we do not support **emojis** in a domain name. Our infrastructure uses the [Python library `idna`](https://github.com/kjd/idna), which [does not compare](https://github.com/kjd/idna/issues/18) IDNA2008 at this stage.
{{%/notice %}}

## DNS management

You can also manage your DNS, via a standard system directly in the **Domains** tab.

To use our DNS servers, specify at your registrar `dns1.alwaysdata.com` and `dns2.alwaysdata.com`.

- [API - DNS registration](https://api.alwaysdata.com/v1/record/doc/)
- [Add DNS record](add-dns)
- [Import zone file](add-dns#importer-un-fichier-de-zone)
- [Add DNS records with CSV](create-dns-records-using-csv)
- [Use external MX](use-external-mx)
- [Change DNS servers](change-of-dns-servers)
- [Add SRV record](add-srv-record)
- [Add CAA record](add-caa-record)
- [Delete DNS record](delete-dns)

{{% notice note %}}
[SOA](https://fr.wikipedia.org/wiki/SOA_Resource_Record) contains a 32-bit number (between 1 and 4294967295). We do not follow the _convention_ to define it with a date format that comes from a period or the zone files were manually edited. Failure to follow this convention _should_ be construed as a mistake.
{{%/notice %}}

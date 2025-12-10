+++
url = "/domains/add-un-registrment-dns/"
title = "How to add a DNS record"
linkTitle = "Add DNS record"
layout = "howto"
weight = 6
tags = [ "dns", "domain" ]
+++

1. Go to **Domains > [example.org] Details - ⚙️ > DNS Records**;
   {{< fig "images/admin-panel_dns-record-list.png" "" >}}

2. Choose **Add DNS record**;

3. Fill in the form.  
   {{< fig "images/admin_panel_add-record.en.png" "" >}}

{{% notice warning %}}
Do not put the root in **Host Name**. For example, by entering `www.example.org` in this box, you will create a record for `www.example.org.example.org`.
{{%/notice %}}

{{% notice note %}}
A record with `@` as host name for some providers matches the empty subdomain. In our case, the **Host Name** box should be empty.
{{%/notice %}}

- [Add SRV record](domains/add-srv-record)
- [Add CAA record](add-caa-record)
- [Use external MX](domains/use-external-mx)

## Import zone file

A DNS zone file is a text file that contains details of all contained DNS records. It follows a standard format, which allows the simple transfer of DNS records from one provider to another.

{{< fig "images/menu.png" "" >}}

This will remove previously added DNS records.

## Resources

- [List of DNS record types](https://fr.wikipedia.org/wiki/Liste_des_enregistrements_DNS)
- [Add DNS records with CSV](create-dns-records-using-csv)

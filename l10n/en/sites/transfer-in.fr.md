+++
url = "/sites/migrer-un-site-chez-alwaysdata/"
title = "Migrate a site to alwaysdata"
layout = "howto"
hidden = true
tags = [ "site" ]
+++

This article explains how to migrate a site to alwaysdata.

{{% notice tip %}}
To facilitate your migration, you can also call on a specific provider: the company (https://www.demenageur-site.com) for example knows our platform and even offers a promo code for a migration to alwaysdata ([contact our support](https://admin.alwaysdata.com/support/add)).
{{%/notice %}}

## Manual transfer

1. Retrieve files and database from the current provider;
   - copy files to your alwaysdata account using [FTP](remote-access/ftp) or [SSH](remote-access/ssh);
   - create the database in **Databases** and import the database into it via a RDBMS client or using `mysql`, `psql` (or more...) depending on the RDBMS used.

2. [Set up the site](sites/add-a-site) in **Web > Sites** with a preproduction address - e.g. account address;
   - modify the configuration files so that everything points to alwaysdata and check the database.

3. Migrate site addresses by editing DNS records for these subdomains and adding addresses to **Web > Sites**.
   - may need to remodify configuration files to avoid redirects to the preproduction address;
   - you can pair it with a [domain transfer] (domains/transfer-a-domain).

{{% notice tip %}}
For commands you can follow the documentation [Move a site](sites/move-a-site).
{{%/notice %}}

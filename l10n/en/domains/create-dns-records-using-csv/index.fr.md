+++
url = "/emails/creer-des-enregistrements-DNS-via-csv/"
title = "How to create multiple DNS records via CSV"
layout = "howto"
hidden = true
tags = [ "dns", "domains" ]
+++

To add multiple DNS records in a single action, go to **Domains > [example.org] details - ⚙️ > DNS records > Add multiple DNS records**.

{{< fig "images/menu.png" "Menu" >}}

The import file should be in [CSV]format (https://fr.wikipedia.org/wiki/Comma-separated_values), that you can create with a spreadsheet software - like Microsoft Excel or LibreOffice Calc. Example:

{{< fig "images/csv-creation.png" "" >}}

The first row of the file must not contain the name of the field of each column. The [API documentation](https://api.alwaysdata.com/v1/record/doc/) takes up all possible options. Fields that are not entered will be set to default.

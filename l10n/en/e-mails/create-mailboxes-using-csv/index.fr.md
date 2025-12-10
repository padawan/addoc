+++
url = "/emails/creer-des-adreses-email-via-csv/"
title = "How to create multiple email addresses via CSV"
layout = "howto"
hidden = true
tags = [ "email" ]
+++

To add multiple email addresses in a single action, go to the **Emails > Addresses > Add multiple email addresses**.

{{< fig "images/menu.png" "Menu" >}}

The import file should be in [CSV]format (https://fr.wikipedia.org/wiki/Comma-separated_values), that you can create with a spreadsheet software - like Microsoft Excel or LibreOffice Calc. Example:

{{< fig "images/csv-creation.png" "" >}}

The first row of the file must not contain the name of the field of each column. The [API documentation](https://api.alwaysdata.com/v1/mailbox/doc/) takes up all possible options. Fields that are not entered will be set to default.

+++
url = "/advance/ip-dediees"
title = "IP addresses assigned"
layout = "man"
hidden = true
tags = [ "email", "http", "site" ]
+++

Whatever the environment is taken[^1], IPv4 addresses are offered through the **Advanced> IP Addresses** menu. These IPs - not shared - are invoiced at €5 including VAT per month or €60 including VAT per year[^2].

## HTTP

Once the IP is taken:

- If the domain is managed on our DNS servers, you can link it to an address via **Advanced > IP Addresses**;
- If the domain uses other DNS servers, create a **DNS record of type A** pointing to the private IP address of your DNS provider.

{{% notice note %}}
This IP will be used for incoming requests, but outgoing requests will always pass through the IP of the HTTP server on which the account is based. This IP is given in the **Advanced> Server Status** menu.
{{%/notice %}}

## SMTP

This IP will be used to send emails.

Once the IP is taken you will be able to tell it which emails should pass through this IP according to the [score they receive from antispam](e-mails/delivery#système-de-notation):

{{< fig "images/dedicated-ip-smtp.en.png" "" >}}

{{% notice note %}}
The lower the note the better the email will be rated.
{{%/notice %}}

[^1]: Available on all our offerings, these IPs are not confused with our [Private Cloud offers](accounts/billing/choose-its-paas).

[^2]: For an annual commitment, contact [support](https://admin.alwaysdata.com/support/add).

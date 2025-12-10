+++
url = "/emails/add-policy-filtering/"
title = "How to add a filter pattern"
linkTitle = "Add filter pattern"
layout = "howto"
weight = 25
tags = [ "email" ]
+++

To better manage emails and sort them automatically, you can use filtering methods. These can be created at the email client or email server level.

{{< fig "images/filter-rule1.png" "Admin interface: go to filtering files" >}}

You will find the list of your entries and will be able to add them.

{{< fig "images/filter-rule2.en.png" "Filter list" >}}
{{< fig "images/filter-rule3.en.png" "Add filter pattern" >}}

Filtering files are translated to the format [Sieve](http://sieve.info/) that you can find in the file `$HOME/admin/mail/[domaine]/[partie-locale]/filter. ieve` on your file space.

{{% notice tip %}}
To create more complicated issues, it will be [Sieve](e-mails/use-sieve-scripts).
{{%/notice %}}

---

- [Resource API](https://api.alwaysdata.com/v1/mailbox/rule/doc/)

+++
url = "/accounts/rename-account/"
title = "Rename account"
layout = "howto"
hidden = true
tags = [ "account" ]
+++

If an account name is no longer suitable (name change, spelling error, etc. ), it is possible to change it.

{{% notice warning %}}
This is a **advanced** feature. Renaming an account changes many elements: default addresses, hostnames to different services, databases, users, or path to the root directory...

As a result, it will _certainly_ need to make configuration changes in your applications and this may make services _temporarily unavailable_.
{{%/notice %}}

Appointment:

- {{< fig "images/public-cloud-list.png" "" >}}

- {{< fig "images/private-cloud-list.png" "" >}}

The new account name will then be requested:

{{< fig "images/account-rename.en.png" "" >}}

{{% notice note %}}
Only the **account owner** can perform this action.
{{%/notice %}}

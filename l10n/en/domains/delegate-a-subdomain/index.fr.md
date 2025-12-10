+++
url = "/domaines/deleguer-un-subdomain/"
title = "How to Delegate a Subdomain"
layout = "howto"
hidden = true
tags = [ "domain", "site" ]
+++

In order to allow another alwaysdata user to use a subdomain of your domain, you must give it your permission.

Pour ce faire, rendez-vous dans **Domaines > Détails de [example.org] - 🔎 > Délégations > Ajouter une délégation**.

{{< fig "images/admin-panel_subdomain-delegation-list.png" "Levels Menu" >}}

{{< fig "images/admin-panel_subdomain-add-delegation.en.png" "Adding a layout: form" >}}

{{% notice info %}}
Do not put the root in **Host Name**. For example, by typing `www.example.org` in this box, you will create a detail for `www.example.org.example.org`.
{{%/notice %}}

{{< fig "images/admin-panel_subdomain-delegation-result.png" "Added a result: result" >}}

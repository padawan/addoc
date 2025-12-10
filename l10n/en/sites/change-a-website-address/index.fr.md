+++
url = "/sites/changer-ladresse-dun-site-web"
title = "Change website address"
hidden = true
layout = "howto"
tags = [ "http", "site" ]
+++

Your site points to an address and you want to use another address/domain. Here are the steps to follow:

In this example, the base address will be `foobar.alwaysdata.net` and the new address `foobar.com`.

{{% notice note %}}
The addresses `.alwaysdata.net` will not be a possible choice.
{{%/notice %}}

{{< fig "images/step1.en.png" "Initial state" >}}

1. Point your domain addresses to our servers:

   - if the domain does not exist, [buy it] (domains/buy-a-domain);
   - if the domain exists, you can:
     - only add [necessary addresses](sites/use-external-addresses) to the website;
     - pass all [technical management](domains/add-an-external-domain) on our DNS servers;
     - [transférer](domains/transfer-a-domain) the domain;
2. Add new addresses to the site in **Web > Sites** - the old one is still available;

{{< fig "images/step2.en.png" "" >}}

3. Change the address at the application level (e.g. its admin interface)

4. Delete the old address in **Web > Sites**. This last point is _not required_, if you do not do the site will remain just accessible on the old address - as long as it points to our servers.

{{< fig "images/step3.en.png" "Final status" >}}

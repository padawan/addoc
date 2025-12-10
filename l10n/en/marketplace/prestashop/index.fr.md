+++
url = "/marketplace/prestashop/"
title = "PrestaShop"
layout = "man"
hidden = true
tags = [ "e-commerce" ]
+++

## Migration from another hosting provider

You will need to edit:

- the `ps_shop_domain`, `ps_shop_domain_ssl` settings set in the `ps_shop_url` and `ps_configuration` tables of the database;
- the **localhost** value of the `physical_URI` parameter of the `ps_shop_url` table by **/**;
- the `$HOME/path/to/application/app/config/parameters.php` file.

## Sending emails

Using `/usr/sbin/sendmail` is not working. Choose to use your own SMTP settings and just specify your SMTP hostname (given in the **Emails > Addresses** menu of your alwaysdata admin interface).

{{< fig "images/prestashop-emails.png" "" >}}

## Enable PrestaShop Cache

If you are experiencing performance issues, a first step may be to enable the **CacheApc** caching system. For this purpose:

- install [PECL extension](languages/php/extensions#depuis-peclhttpspeclphpnet) `apcu` on your account via [SSH](remote-access/ssh).

```
peel_install_apcu
```

- then add [the extension in your `php.ini`](languages/php/configuration#paramètres-phpini).

```
extension=/home/[compte]/path/to/apcu-[VERSION].so
```

- then activate the **API cache** system in the PrestaShop administration interface (Advanced Settings > Performance).

{{% notice warning %}}
`[VERSION]` matches the major version of PHP with which the extension was installed. By default, this will take the version of the **Environment** menu (used in SSH). You can install it with [another version of PHP](languages/php/troubleshooting#utiliser-différentes-versions-en-ssh) if your website uses another one.
{{%/notice %}}

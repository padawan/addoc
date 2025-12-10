+++
url = "/en/data-bases/memcached/php/"
title = "How to configure a PHP application with Memcached"
hidden = true
layout = "howto"
tags = [ "database", "memcached", "php" ]
+++

## Setup

Using Memcached in PHP requires [installing a PECL extension](languages/php/extensions#depuis-peclhttpspeclphpnet) on your account via [SSH](remote-access/ssh).

```
$ ad_pecl memcached
```

Don't forget to [add the extension in your `php.ini`](languages/php/configuration#paramètres-phpini):

```
extension=/home/[compte]/path/to/memcached-[VERSION].so
```

{{% notice warning %}}
`[VERSION]` matches the major version of PHP with which the extension was installed. By default, this will take the version of the **Environment** menu (used in SSH). You can install it with [another version of PHP](languages/php/troubleshooting#utiliser-différentes-versions-en-ssh).
{{%/notice %}}

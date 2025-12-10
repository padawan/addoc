+++
url = "/en/languages/php/installer-un-package/"
title = "How to install a PHP package"
hidden = true
layout = "howto"
tags = [ "php" ]
+++

## Package Management

Several tools exist in PHP to install packages.

### Dial

[Composer](https://getcomposer.org/) allows local installation of a set of dependencies. It is preinstalled at alwaysdata.

To install listed dependencies in the `composer.json` file:

1. To use _Compose 2_ (latest versions):

```sh
$ compose install
```

or

```sh
$ composer2 install
```

2. To use _Dial 1_:

```sh
$ composer1 install
```

### PEAR

[PEAR](https://pear.php.net/) is one of the oldest package management tools for PHP. It is not preinstalled, but you can download it and execute:

```sh
$ wget http://pear.php.net/go-pear.phar
$ php go-pear.phar
```

{{% notice info %}}
The PHP executable specified at the PEAR binary level does not take into account the necessary extensions (XML for example). These paths should be changed and `/usr/bin/php` instead of `/usr/alwaysdata/php/[VERSION]/bin/php`.
{{%/notice %}}

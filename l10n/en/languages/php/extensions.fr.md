+++
url = "/en/languages/php/installer-une-extension/"
title = "How to install a PHP extension"
hidden = true
layout = "howto"
tags = [ "php" ]
+++

`[compte]` and `[extension]` are to be replaced by the name of the extension to install and the account on which it must be installed.

## Extension Management

A PHP extension is intended as a file with the `.so` extension. To load it you will need to add it to your `php.ini` (**Environment > PHP** or at the site level in **Web > Sites**).
{{% notice warning %}}
Some extensions load with `zend_extension` directive rather than extension, it is the extension editor that will tell you when this directive should be used instead.

The extensions depend on the major version of PHP. In other words, a `.so` file compiled for PHP 5.5 will not work with 5.6: **it will need to be recompiled**.
{{%/notice %}}

The following sections show you how to get new extensions. All commands are executed in [SSH](remote-access/ssh).

### Extensions included in PHP

PHP includes many standard extensions, many of which are already preloaded by default by alwaysdata. To see the full list of available extensions:

```sh
$ ls $(php-config --extension-dir)
```

To see the list of already loaded extensions on your account:

```sh
$ grep extension $HOME/admin/config/php/php.ini
```

To load an extension included in PHP, you will not need to specify the full directory, only the filename is enough:

```
extension = [extension].so
```

> Examples: `imap`, `intl`.

### From PECL

Many extensions can be installed via [PECL](https://pecl.php.net/). To install an extension, we suggest using our in-house script, `ad_install_pecl`. It will download, configure and compile an extension:

```sh
$ ad_install_pecl [extension]
```

The command manages a new `.so` file in the current directory. At the end of the script, it gives a path to add to `php.ini`. For example if this is run at the root of the account:

```ini
extension = /home/[compte]/[extension].so
```

or `/home/[compte]/[extension].so` is the absolute path to your extension.

However, you can do without our script and use the usual commands (`phpize`, `make`) if you prefer.

> Example of PECL extensions successfully requested: `apcu`, `imagick`, `memcached`, `ssh2`, `yaml`.

### From Publisher Site

Some extensions are directly downloadable from the publisher's website in precompiled form (`.so` file). If the editor offers you the choice, you will need to download the 64 bit Linux version. For example:

- [ionCube](https://www.ioncube.com/loaders.php)
- [SourceGuardian](https://www.sourceguardian.com/loaders.html)
- [Zend Guard](http://www.zend.com/en/products/guard/downloads#Linux)

Then add the absolute path to the `php.ini`. For example if it is downloaded to the root of the account:

```ini
extension = /home/[account]/[extension].so
```

### From distribution packages

Some extensions are complex or impossible to compile by hand. It is possible to recover a `.so` from Linux distribution packages, e.g. [Debian](https://www.debian.org/distrib/packages):

```sh
$ wget http://ftp.debian.org/debian/pool/main/m/mapserver/php5-mapscript_7.0.4-1~bpo8+1_amd64.deb
$ dpkg-deb -x php5-mapscript_7.0.4-1~bpo8+1_amd64.deb .
```

Then add the absolute path to the `php.ini`. For example if it is downloaded to the root of the account:

```ini
extension = /home/[account]/[extension].so
```

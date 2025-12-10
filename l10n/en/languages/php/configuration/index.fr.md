+++
url = "/en/languages/php/configuration/"
title = "Configure PHP"
hidden = true
layout = "man"
tags = [ "php" ]
+++

## Supported Versions

|                                                                                                                                                  |
| ------------------------------------------------------------------------------------------------------------------------------------------------ |
| 8.5 \\| 8.4 \\| 8.3 \\| 8.2 \\| 8.1 \\| 8.0 |
| 7.4 \\| 7.3 \\| 7.2 \\| 7.1 \\| 7.0                          |
| 5.6 \\| 5.5 \\| 5.4 \\| 5.3 \\| 5.2                          |
| 4.4                                                                                                                              |

The default version can be changed in the alwaysdata administration, **Environment > PHP**. This version is especially used when you start `php`.

Versions are not forcefully [already installed](languages#versions).

## Parameters (php.ini)

The default `php.ini` file activates several essential extensions and defines some basic parameters. This file is readable at the `$HOME/admin/config/php/php.ini` location. Here's its content (for an account configured on PHP 8.2 version):

```ini
; Core settings
max_execution_time = 120
max_input_time = 60
memory_limit = 256M

post_max_size = 256M
upload_max_filesize = 256M

output_buffering = 4096
expose_php = Off
default_socket_timeout = 10
date. imezone = "Europe/Paris"

log_errors = On
error_log = /home/test/admin/logs/php/php. og
ignore_repeated_errors = On
ignore_repeated_source = On


mysql.default_socket = /run/mysqld/mysqld.sock

session. ave_path = /home/test/admin/tmp
upload_tmp_dir = /home/test/admin/tmp

; Extensions
extension_dir = "/usr/alwaysdata/php/8. /lib/php/extensions/no-debug-non-zts-20220829"

extension = ctype.so
extension = curl.so
extension = dom.so
extension = gd. o
extension = gettext.so
extension = iconv.so
extension = json.so
extension = mbstring.so
extension = openssl.so
extension = posix. o
extension = simplexml.so
extension = tokenizer.so
extension = xml. o
extension = xmlwriter.so
extension = xsl.so
extension = zip.so
extension = zlib. o

extension = mysqli.so
extension = pgsql.so
extension = pdo.so
extension = pdo_mysql.so
extension = pdo_pgsql.so

extension = fileinfo. o
extension = phar.so

; Zend extensions
zend_extension = /usr/alwaysdata/php/8.2/lib/php/extensions/no-debug-non-zts-20220829/opcache.so
opcache.lockfile_path = /home/test/admin/tmp
```

If you want to change this `php.ini`, you can do so in the **Environment > PHP** section (or at the site level in **Web > Sites**). Any directives you define will be appended to the initial `php.ini` file, and can overwrite the values by default. There is no limitation to what you can find, all PHP options are accessible.

You can also create `.user.ini` files to apply parameters only to certain directories.

## HTTP Deployment

For a PHP application to be accessible via the web, create a site in the **Web > Sites** section of the alwaysdata administration by choosing the type **PHP**.

{{< fig "images/php-type.png" "">}}

### Version management

Geeking PHP versions per site means greater RAM consumption because sites cannot share PHP processes with each other. It is therefore preferred:

- to deprive account management of PHP (section **Environment**);
- use few different versions per account;
- if one has to use more and a certain number of sites use the same version, group their php. nor via the global php.ini and pass them to the PHP version by default.

+++
url = "/forward/migrations/software-architecture-2017/"
title = "Software Architecture 2017"
layout = "man"
hidden = true
tags = [ "infrastructure", "migration" ]
+++

This migration groups many changes with the main objectives:

- global update of preinstalled software;
- simplifying certain aspects of our software infrastructure.

For older mutual accounts, this migration also includes migration to our own corporate infrastructure.

This document describes the main incompatibilities introduced by this migration. We strive to be as complete as possible, but it is impossible to be absolutely exhaustive. We strongly invite you to conduct a migration test to detect as many incompatibilities as possible.

This document does not describe the new features contributed by the 2017 software infrastructure, which was done in a dedicated [blog article](https://blog.alwaysdata.com/2017/01/24/python-3-6-ruby-2-4-and-others/).

## Geaelite

- You must not use the new hostname format to access services [introduced in 2015](https://blog.alwaysdata.com/2015/03/05/change-of-hostname-for-access-to-our-services/). You will find the addresses to use in the alwaysdata administration in each relevant section. Old formats, using the `alwaysdata.com` domain (e.g. `mysql.alwaysdata.com` or `postgresql1.alwaysdata. om`), or a dot between the service name and the account name (e.g. `mysql.accounte.alwaysdata.net`) will stop working.

- Multiple files and directories located in each account are moved or deleted. In particular:
  - the 4 default files (`php5.fcgi`, `php5.ini`, `php4.fcgi`, `php4.ini`) from the `$HOME/cgi-bin` directory are removed, and the directory is also empty and empty;
  - the different internal configuration files (`$HOME/.env.*`, `$HOME/admin/apache`) are moved to an$HOME/admin/config\` directory;
  - `$HOME/admin/ssl`, `$HOME/admin/session` and `$HOME/admin/log/awstats` are removed;
  - logs are stored in the directory `$HOME/admin/logs`, with one subdirectory per type (`http`, `apache`, etc.). The old log directory (`$HOME/admin/log`) is moved to `$HOME/admin/logs/old`.

## Languages

### PHP

- The `.php4` and `.php5` file extensions are no longer supported, only `.php` files are interpreted by PHP by default. You can still retrieve the old behavior by creating a `.htaccess` file at the root of your account. For example, for `.php5` files to be interpreted by PHP, it will need to contain:

```
AddHandler fcgid-script .php5
FCGIWrapper /usr/bin/php-cgi .php5
```

- It is no longer possible to run PHP 4 and PHP 5 at the same time. PHP 4 is just like having a PHP version like any other, without any specificity.

- Versions 5.5.0, 5.5.1 and 5.5.6 are replaced by 5.5.19.

- The only PHP binary available is `php`. Do not use `php-cgi` anymore.

- Non-standard extensions (APC, Xapian, Xdebug and Mapscript for PHP 5.3 and 5.2 and Fileinfo in 5.2) are removed. However, you can [install yourself](languages/php/extensions) in your own account.

- Symfony is no longer preinstalled, you will need to [manually install it](languages/php/packages).

- The `calendar` and `intl` extensions are no longer automatically enabled, they will have to be explicitly loaded into your `php.ini` if necessary.

- Some minor compilation options have been changed.

- The internal Apache directives that configure PHP (in FastCGI) have been changed. This only matters if you explicitly refer to it, e.g. if you have a _customized_ site and copied the directives from the internal Apache configuration. We would like you to replace your _Apache customized_ sites with _Apache standard_ sites and put your own directives in the _Additional virtual host guidelines_ field (in _Advanced configuration_) or in a ` file. taccess`.

### Python

- The only Python binary available is `python`. Do not use `python2.6` anymore. You will need to think about replacing your shebangs (first line of a script, e.g. `#!/usr/bin/python`) if they do not already use `python`.

- Some of the previously preinstalled libraries are removed, including Django. So you need to [manually install] (languages/python/configuration#environnement) all the bibliotheks you will need.

- _WSGI_ applications are served by [uWSGI](http://uwsgi-docs.readthedocs.io/en/latest/) instead of [mod_wsgi](https://modwsgi.readthedocs.io/en/develop/). In the vast majority of cases this will not change anything for you. If you had compiled your own mod_wsgi with a _custom Apache site_, it will continue to work.

- Version 2.5.5 is replaced by 2.5.6, 2.6.6 by 2.6.9 and 3.1 by 3.3.6.

### Ruby

- The only Ruby binary available is `ruby`. Do not use `ruby1.8` anymore. You will need to think about replacing your shebangs (first line of a script, e.g. `#!/usr/bin/ruby`) if they do not already use `ruby`.

- The few previously preinstalled libraries are removed, including Ruby on Rails. So you need to [manually install] (languages/ruby/configuration#environnement) all the bibliotheks you will need.

- The _Ruby Rack_ or _Ruby on Rails_ applications are served by [uWSGI](http://uwsgi-docs.readthedocs.io/en/latest/) and no longer [Passenger](https://www.phusionpassenger.com). In the vast majority of cases this will not change anything for you. If you compiled your own Passenger with a _custom Apache site_, it will continue to work.

- Versions 1.8.6 and 1.8.7 are replaced by 1.8.7-p374 and 1.9.2 by 1.9.2-p320.

## Databases

### MySQL

We replace MySQL with MariaDB 10.1, which is perfectly compatible with MySQL. MariaDB 10.1 matches MySQL 5.6 or even 5.7. For more details on compatibility:
https://mariadb.com/kb/en/mariadb/mariadb/mariadb-vs-mysql-compatibility/

### PostgreSQL

We update PostgreSQL to version 9.6:
https://www.postgresql.org/docs/9.6/static/release.html

We also update PostGIS to 2.3:
http://postgis.net/docs/manual-2.3/PostGIS_Special_Functions_Index.html#NewFunctions

### MongoDB

We are upgrading MongoDB to version 3.2:
https://docs.mongodb.com/manual/release-notes/

Warning: Authentication mechanism changes. Users with all permissions have the `readWrite` role, users with read-only permissions have the `read` role.

### LayDB

We update CouchDB to version 1.6: https://docs.couchdb.org/en/stable/whatsnew/1.6.html#version-1-6-0

## Misc

### Apache

- [Apache](https://httpd.apache.org) is updated to version 2.2.32

- `index.htm`, `index.cgi`, `index.pl` and `index.xhtml` are no longer indexed as indexes. Only `index.php` and `index.html` are and `index.php` becomes a priority on `index.html`.

- If no index file is present, a _Forbidden_ error page will be displayed rather than listing the files.
  They can re-add it to a _.htaccess_ file of the `Options +Indexes` directive.

- The `mod_dav_svn`, `mod_wsgi` and `Passenger` modules are removed.

- Files from other modules are moved, but the migration will automatically change the path of `LoadModule` directives in _Apache customized_ sites that refer to it. So you don't have to worry about it.

### Various updates

Numerous applications and bibliotheques are also updated. They are too numerous to all listed, but among the most notable ones, likely to cause incompatibilities:

- Erlang 19.1 (previously in 15.b)
- Haskell 7.10 (previously in 6.8)
- GDAL 1.10 (previously in 1.5)
- git 2.9 (previously in 1.8)
- ImageMagick 6.8 (earlier in 6.5)
- Java Java 7 and 8 (previously in 6)
- Lua 5.3 (previously in 5.1)
- MapServer 7.0 (previously in 5.6)
- Mercurial 3.9 (previously in 1.3)
- OCaml 4.01 (previously in 3.10)
- Perl 5.20 (previously in 5.10)
- PROJ 4.8 (previously in 4.7)
- Subversion 1.8 (previously in 1.6)
- Texlive 2014 (formerly in 2007)

### VPS/dedicated environment

The following services, installed on request, will also be updated:

- RabbitMQ is updated to version 3.5
- Redis is updated to version 3.2
- Elasticsearch is updated to version 5.5

### Older bibliotheques disappear

If you had compiled your own apps, they are likely to be linked to bibliotheques or versions that have disappeared (due to a jump from the BIA). Your applications, or some functionality, may then stop working. You will then have to recompile the applications in question.

Among the most likely bibliotheks affected:

- [OpenSSL](https://www.openssl.org). However, version 0.9.8 is still installed, in conjunction with version 1.0.2, so your applications will continue to work. However, since version 0.9.8 is old, it is highly recommended to recompile your unwanted applications to use a recent version of OpenSSL.
- free adline

## HTTP Server IP Change

For some users still hosted in our old master infrastructure, the IP address of their HTTP server will be changed. This will be indicated, as the case happens, on the migration details page in the alwaysdata administration. If you use our DNS servers or a CNAME, you will not need to do anything. However, if you had manually defined a DNS record of type A or AAAA, you will need to change them after migrating to specify new IP addresses.

Older IPs will continue to work for more weeks (_reverse proxy_ working), but going through them implies a low increase in the latency of your sites and an increase in the risk of failures. It is therefore highly recommended that they be changed as soon as possible.

## Migration Test

It is highly recommended that you run a migration test predominantly to ensure that your applications will continue to work, and to correct them otherwise.

### SSH Access

You will be able to connect to your SSH account on a temporary server. This server is equipped with the 2017 software architecture, but **it can access your real files**, not a copy. Any changes you make will be posted to your account.

SSH access can be slowed down compared to the normal SSH server. This is a test advice, but this slowness will disappear after the actual migration.

### HTTP Access

You can test your sites in several ways:

- by accessing it via the usual URL, to which you will add the suffix `.migration.alwaysdata.net`. For example, if your site is normally accessible at `www.example.org`, you can access it on the test infrastructure by going to `www.example.org.migration.alwaysdata.net`.
  Warning: SSL certificate returned on the address `*.migration.alwaysdata.net` will not be valid, you will have to explicitly authorize it by your browser. This only concerns the test of migration, not real migration, for which certificates will not change.
  Warning: some applications are redirecting to the nominal URL, which requires testing using this method.

- using a browser extension to force the `Host` header (hence the requested site). For example under Chrome, the extension [Virtual Hosts](https://chrome.google.com/webstore/detail/virtual-hosts/aiehidpclglccialeifedhajckcpedom). You will need to log in by entering the HTTP test server address (for example, `migration-test1.paris1.alwaysdata.com`), but asking your site address.

- by modifying your `hosts` file to force use the HTTP test server IP to connect to your sites. This can be done by directly editing the relevant file, or by means of a browser extension, for example HostAdmin on Firefox.

Your applications will then be started on a temporary server running the 2017 software infrastructure, as if the migration had taken place. As in SSH, the files in your account this server has access to are your real files. Access can also be slowed down, so ignore this.

Warning: The internal configuration of your alwaysdata account on this temporary server is managed at the time you run the test migration. It is not changed afterwards. For example, if you run the test migration while the PHP version defined in your environment is 5.6. 7, and then you modify this version, this change will not be performed on the temporary migration server. You will then have to run a test migration again to take the change into account. Meme for the changes you make in the Web section > Sites.

### Databases

When running the test migration All of your databases and database users are copied to a temporary server, running new versions. You will then be able to access your data copied to this server using your usual credentials to perform your tests. Unlike the files used by the SSH and HTTP servers, you work here on a copy of your data. At each execution of the test migration, your previous copies are overwritten by new ones.

## Migration help

### GEOM_GEOM_SURFACE

It may be tempting to take advantage of migration to make drastic changes to your web applications, their configuration or deployment. Instead, we recommend that you make as few changes as possible to make the migration unfold with success (after testing it), and make major changes only after your account is on the new infrastructure.

The major integer to do this is that once your account is on the new infrastructure you will be able to discover new options and widely simplified deployment methods, especially with Python and Ruby. For example, if you compiled your own interpreter or Apache modules (mod_wsgi, Passenger), you will most likely be able to do without it once your account is on the new infrastructure.

### You have PHP relative Apache configuration references

You have references to the PHP internal configuration either in a ` file. taccess`, or in a _custom Apache site_ (maybe you copied some configuration pieces from `sites.conf` file). For example, you have references to `application/x-httpd-fastphp5`.

Since our internal PHP configuration has changed, your configuration will stop working. If you are using PHP and a _custom Apache site_, we invite you to convert it to a _standard Apache site_ and specify your specific Apache directives either in a ` file. taccess`, or in the _Additional virtual host guidelines_ field.

### Error: "cannot open shared object file: No such file or directory"

This error indicates that a system library is missing. While the vast majority of updated system bibliotheques on the new infrastructure remain compatible with older versions (because ABI remains the me), some are not (there is an ABI's version jump). If your applications depend on these libraries, they will no longer find them.

The following bibliotheques are concerned:

- [libgmp](https://gmplib.org)
- free adline
- [libtiff](http://www.libtiff.org/)

In general, these libraries are not used directly by applications, but by dependencies (Python module, gem Ruby, PHP extension). Recompiling these modules on the new infrastructure will allow them to use the new version of the bibliotheque, but they will no longer work on the old infrastructure.

Another solution is sometimes possible: indicate when compiling the module to disable some features to prevent it from using the relevant library. For example, you can compile module [Pillow](https://python-pillow.org/) without support for TIFF files in this way:

```
$ pip install Pillow --global-option="build_ext" --global-option="--disable-tiff"
```

### Migrate a Python application to FastCGI

You have a Python application (for example, using [Django](https://www.djangoproject.com/)) that works with FastCGI, with a `.htaccess` file and a `.fcgi` script. FastCGI will continue to work on the new infrastructure as before, but if you are not using a virtualenv you will need to manually install the Python system libraries because they are no longer preinstalled on the new infrastructure.

- in SSH, install all the bibliotheques you need, for example:

    ```
    $ mkdir $HOME/python_libs; PYTHONPATH=$HOME/python_libs easy_install --always-copy --install-dir $HOME/python_libs Django==1.6 flup==1.0.3.dev-20110405 psycopg2==2.0.11
    ```

- edit your ` file. cgi` to replace the shebang (the first line), usually `#!/usr/bin/python`, with `#!/usr/bin/eval PYTHONPATH=/home/foo/python_libs python`, `foo` having to replace with your account name.

### You are using your own mod_wsgi module

You compiled your own Python interpreter and [mod_wsgi]module (https://modwsgi.readthedocs.io/en/develop/), which you use with a _custom Apache site_. Make sure you have defined the Apache directive _WSGIPythonHome_, otherwise you may have errors with the new infrastructure, for example:

```
ImportError: No module named _sysconfigdata_nd
```

If your Python interpreter is in the `/home/foo/python` directory, then you should have used the directive:

```
WSGIPythonHome /home/foo/python
```

### You are using the system mod_wsgi module

You have a _custom Apache site_ that loads the system module `/usr/lib/apache2/modules/mod_wsgi.so-2.6`. As mentioned above, this module disappears on the new infrastructure (for the benefit of WSGI). To simplify migration, you can:

- download https://files.alwaysdata.com/migrations/software-2017/mod_wsgi.so-2.6 to your account:

    ```
    wget https://files.alwaysdata.com/migrations/software-2017/mod_wsgi.so-2.6
    ```

- replace `/usr/lib/apache2/modules/mod_wsgi.so-2.6` in your _custom Apache directives_ with the file path to your account, e.g. `/home/foo/mod_wsgi.so-2.6`.

+++
url = "/forward/migrations/software-architecture-2020/"
title = "Software Architecture 2020"
layout = "man"
hidden = true
tags = [ "infrastructure", "migration" ]
+++

This migration consists mainly of a general update of the software available on our servers. It involves moving the account to new servers - running with the 2020 architecture. **All** servers (HTTP, SSH, databases, etc) are likely to change.

## Why should migration be imposed?

The main purpose of the architecture migration is to upgrade our servers to a newer version of their operating system (Debian). It is important to proceed to these updates for two reasons:

- the security. Old software versions are not supported by their authors or distributors eternally. When a software stops supporting, it continues to work, but new security vulnerabilities are no longer fixed. Continuing to use these old versions would therefore pose a serious risk to the security and reliability of your applications and data.

- to be able to use recent versions of software. The older an operating system is, the more difficult it is to run recent software. To continue offering you the latest versions of the software we offer (or that you can install yourself in your account), it is important to have a relatively recent version of the operating system.

These infrastructure migrations are carried out approximately every four years. This corresponds to the hard life of a Debian release (from [five years](https://wiki.debian.org/LTS), but it is necessary to count the incompressible internal development time before switching to new versions). This seems to us to be a good balance, avoiding excessive migrations, but allowing to run the virtual totality of the recent software.

---

This document describes the major incompatibilities introduced by this migration. We strive to be as complete as possible, but it is impossible to be absolutely exhaustive.

## Apache

Apache _2.2_ is no longer available. Accounts that used this version will automatically switch to [Apache _2.4_](https://httpd.apache.org/docs/2.4/fr/).

Global guidelines added by our users, in **Web > Configuration**, or in the configuration of a **custom Apache site**, will be sorted out **after** the default directives. This allows our users to overwrite these directives by default.

## Databases

### MySQL

MariaDB is updated to [version 10.4](https://mariadb.com/kb/en/release-notes-mariadb-104-series/).

### PostgreSQL

PostgreSQL is updated to [version 12](https://www.postgresql.org/docs/12/release-12.html).

### MongoDB

MongoDB is updated to [version 4.2](https://www.mongodb.com/docs/v5.3/release-notes/4.2/).

### LayDB

CouchDB is updated to [version 3.0](https://docs.couchdb.org/en/stable/whatsnew/3.0.html#version-3-0-0).

## Languages

To determine the current version of your account: log in via [SSH](remote-access/ssh) and run `cat /etc/debian_version`.

### PHP

| Available versions on v2020 - Debian Buster (10.X) | Available releases on v2017- Debian Jessie (8.X) |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `4.4.9`                                                                               | `4.4.9`                                                                             |
| `5.2.17`                                                                              | `5.2.17`                                                                            |
| `5.3.29`                                                                              | `5.3.29`                                                                            |
| `5.4.45`                                                                              | `5.4.45`                                                                            |
| `5.5.38`                                                                              | `5.5.38`                                                                            |
| `5.6.40`                                                                              | `5.6.38` `5.6.37`                                                                   |
| `7.0.33`                                                                              | `7.0.31` `7.0.32`                                                                   |
| `7.1.33`                                                                              | `7.1.21` `7.1.23` `7.1.24` `7.1.26` `7.1.32`                                        |
| `7.2.29` `7.2.31` `7.2.32` `7.2.33` `7.2.34`                                          | `7.2.9`  `7.2.11` `7.2.12` `7.2.14` `7.2.22`                                        |
| `7.3.16` `7.3.18` `7.3.20` `7.3.22` `7.3.24` `7.3.26`                                 | `7.3.0`  `7.3.1`  `7.3.9`                                                           |
| `7.4.4`  `7.4.6`  `7.4.8`  `7.4.10` `7.4.12` `7.4.14`                                 | `7.4.0`  `7.4.3`                                                                    |
| `8.0.0`  `8.0.1`                                                                      | `-`                                                                                 |

- Minor deleted versions are automatically replaced by the closest minor version (7.4.4 for example 7.4).
- The `bcmath`, `calendar`, `exif`, `ftp`, `soap`, `xmlreader`, `xmlrpc` and `zip` extensions are automatically loaded. You can remove explicit loading directives from your custom _php.ini_ if you wish.

### Python

| Available versions on v2020 - Debian Buster (10.X) | Available releases on v2017- Debian Jessie (8.X) |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `2.4.6`                                                                               | `2.4.6`                                                                             |
| `2.5.6`                                                                               | `2.5.6`                                                                             |
| `2.6.9`                                                                               | `2.6.9`                                                                             |
| `2.7.17` `2.7.18`                                                                     | `2.7.15` `2.7.16` `2.7.18`                                                          |
| `3.3.7`                                                                               | `3.3.7`                                                                             |
| `3.4.10`                                                                              | `3.4.9`  `3.4.10`                                                                   |
| `3.5.9`  `3.5.10`                                                                     | `3.5.6`  `3.5.9`                                                                    |
| `3.6.10` `3.6.11` `3.6.12`                                                            | `3.6.7`  `3.6.8`  `3.6.10`                                                          |
| `3.7.7`  `3.7.8`  `3.7.9`                                                             | `3.7.0`  `3.7.1`  `3.7.2`  `3.7.7`                                                  |
| `3.8.2`  `3.8.3`  `3.8.4` `3.8.5` `3.8.6` `3.8.7`                                     | `3.8.0`  `3.8.3`                                                                    |
| `3.9.0`  `3.9.1`                                                                      | `-`                                                                                 |

- Minor deleted versions are automatically replaced by the nearest minor version (3.8.2 for example for 3.8). If you had created `virtualenvs` with these versions, you will have to recreate them.

When changing mines, rather than recreating the virtual environment, you can use the following command:

```
python -m venv --upgrade [myenv]/
```

### Ruby

| Available versions on v2020 - Debian Buster (10.X) | Available releases on v2017- Debian Jessie (8.X) |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `1.8.7-p374`                                                                          | `1.8.7-p374`                                                                        |
| `1.9.3-p551`                                                                          | `1.9.2-p3201` `1.9.3-p551`                                                          |
| `2.0.0-p648`                                                                          | `2.0.0-p648`                                                                        |
| `2.1.10`                                                                              | `2.1.10`                                                                            |
| `2.2.10`                                                                              | `2.2.10`                                                                            |
| `2.3.8`                                                                               | `2.3.8`                                                                             |
| `2.4.9` `2.4.10`                                                                      | `2.4.5`                                                                             |
| `2.5.7` `2.5.8`                                                                       | `2.5.3`      `2.5.5`                                                                |
| `2.6.5` `2.6.6`                                                                       | `2.6.0`      `2.6.2`                                                                |
| `2.7.0` `2.7.1` `2.7.2`                                                               | `-`                                                                                 |
| `3.0.0`                                                                               |                                                                                     |

- Minor deleted versions are automatically replaced by the nearest minor version (2.6.5 for example 2.6).

### Node.js

| Available versions on v2020 - Debian Buster (10.X) | Available releases on v2017- Debian Jessie (8.X) |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `6.17.1`                                                                              | `6.14.4` `6.16.0`  `6.17.0`                                                         |
| `8.17.0`                                                                              | `8.11.4` `8.12.0`  `8.15.0`  `8.15.0`                                               |
| `9.11.2`                                                                              | `9.11.1`                                                                            |
| `10.19.0` `10.20.1` `10.23.1`                                                         | `10.9.0` `10.12.0` `10.13.0` `10.15.1` `10.15.3`                                    |
| `11.15.0`                                                                             | `11.0.0` `11.1.0`  `11.8.0`  `11.12.0`                                              |
| `12.16.1` `12.16.3` `12.20.1`                                                         | `12.0.0` `12.14.0`                                                                  |
| `13.11.0` `13.14.0`                                                                   | `-`                                                                                 |
| `14.2.0`  `14.5.0` `14.11.0` `14.15.1` \`14.15.4      | `-`                                                                                 |
| `15.0.0`  `15.2.1` `15.6.0`                                                           | `-`                                                                                 |

- Minor deleted versions are automatically replaced by the nearest minor version (12.16.1 for example for 12).

### Elixir

| Available versions on v2020 - Debian Buster (10.X) | Available releases on v2017- Debian Jessie (8.X) |
| ------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------- |
| `1.11.1` `1.11.2` `1.11.3`                                                            | `-`                                                                                 |
| `1.10.2` `1.10.3` `1.10.4`                                                            | `-`                                                                                 |
| `1.9.4`                                                                               | `-`                                                                                 |
| `1.8.2`                                                                               | `-`                                                                                 |
| `1.7.4`                                                                               | `1.7.3` `1.7.4`                                                                     |
| `1.6.6`                                                                               | `1.5.3` `1.6.6`                                                                     |

- Minor deleted versions are automatically replaced by the nearest minor version.

### Java

Java will soon become a major language that can be administered through the administration interface.

- Available versions are `8.0.41`, `11.0.28` and `14.0.36`. Version 7, 9 and 10 are deleted.

- Default version becomes `11`. This version will be executed when using the `java` binary.

- Until now, to use a specific version of Java, you could fetch the binary in `/usr/lib/jvm`. This is no longer possible: you can force a different version by defining the `JAVA_VERSION` environment variable. For example, to run version 8: `JAVA_VERSION=8 java`.

## Misc

- _TLS 1.0_ and _1.1_ are now **disabled by default** on the HTTP protocol, as older protocols present security vulnerabilities. You can re-enable them by going to **Web > Configuration > SSL**, then choosing the **Old** configuration.

- The directory of temporary **(TEMPDIR)** files becomes `~/admin/tmp` rather than `/tmp`. PHP sessions, for example, are created in this directory.

- For Node type sites. s, Elixir and User Program, the internal IP (defined in the `IP` environment variable) on which your application should listen will change and switch to **IPv6**. The new IP will be given in the website command helptext.

- The `ALWAYSDATA_HTTPD_PORT` and `ALWAYSDATA_HTTPD_IP` environment variables are no longer available, you will need to use `PORT` and `IP`.

- The `PATH` environment variable will always contain local paths for different languages, e.g. `~/. ocal/bin`, `~/npm-packages/bin`, etc., including SSH non-login or non-interactive connections, and in your HTTP applications.

- The owner user of your `$HOME` personal directory (e.g. `/home/foobar`, if your account is called _foobar_), previously identical to your username (e.g. `foobar`), becomes `root`. The proprietary group remains the same as your username (here, `foobar`), so nothing will change in practice. The permissions of your personal directory will be reset to 0770.

- Language binaries are now installed on demand. In this case you would need, for example, `/usr/alwaysdata/python/2.7.18/lib/libpython2.7.so`, make sure that you run `python` in 2.7.18 at least once.

### Various updates

A lot of software and bibliothetics will be updated (our servers run Debian Buster, previously Debian Jessie). Among notable updates:

- Erlang 21.2 (formerly 19.2)
- GDAL 2.4 (previously 1.10)
- git 2.20 (previously 2.19)
- GB 1.11 (previously 1.7)
- MapServer 7.4 (previously 7.0)
- Mercurial 4.8 (formerly 3.9)
- PROJ 5.2 (previously 4.8)
- QGIS 3.4 (formerly QGIS 2.4)

### VPS/dedicated environment

The following services, when installed, will be updated:

- _RabbitMQ_, version 3.7.8
- _Redis_, version 5.0

Version mounts of _MySQL_ (not MariaDB) and _ElasticSearch_ will be viewed on a case-by-case basis with users.

Only versions of _explicitly used_ languages, either in the **Web > Sites** section, or in the **Environment** section, will be uninstalled on the system. For example, if not the default Python version (defined in **Environment > Python**), or none of your sites (**Web > Sites**) use Python 2. .6, then this version will no longer be preinstalled. However, it will be automatically installed if you create a site with this version of Python, or you change the version of Python to the default.

## Preparing for migration

A number of actions can be performed on the 2017 architecture - Debian Jessie (8.X):

- switch to _Apache 2.4_ in the **Web > Configuration > Apache** tab;

- change [TLS] (security/ssl-tls/configure-tls) to switch to _Intermitting_ configuration in the **Web > Configuration > SSL** tab;

- replace in your applications the `ALWAYSDATA_HTTPD_PORT` and `ALWAYSDATA_HTTPD_IP` environment variables with `PORT` and `IP`;

- change language versions to switch to _last minors_. This happens in the **Environment** menu and/or at the level of your sites in **Web > Sites**. For example, you can switch to PHP 7.3.9 instead of PHP 7.3.0.

We strongly urge you to make these changes in production before you migrate.

### Databases

At the same time as the Buster migration, we provide basic data migrations. You can use the [tester](advanced/migrations/perform-migration) via the **Tester** button. All of your databases and database users are copied to a temporary server, running new versions.

Shared server users can do these tests at the same time as the Buster migration. Migration Buster will close other migrations.

For VPS and dedicated server users, the test of database migration is linked to the Buster migration. The **Tester** button will only **copy** the databases on the test server. Regarding HTTP deployment refer to paragraph [Preparing Migration](advanced/migrations/2020-software-architecture#préparation-de-la-migration).

## Migration unfolding

When you click the **Migrate** button, the process snaps into effect immediately, but sometimes a few minutes later depending on the number of users that migrate at the same time. Migration takes place in multiple steps, **service per service**. For example, your files will be migrated before your databases.

- Migrating your files, done first, will cause your websites to unavailable (which will display an _internal error_), of your planned tasks of your remote access (SSH, FTP, etc. ). However, the cut is **short duration** (few seconds in handle, more if you have tens of thousands of files), because your files are **precopies** to preset.

- When migrating databases, the **connection to databases is switched off**. There is an average of 1 minute unavailability per GB of data. It may be appropriate to set up a _static maintenance page_ on your websites to avoid a general error connecting to databases.

It is possible to know if the migration is finished via the _[Tâches]menu (https://admin.alwaysdata.com/task)_ (top right of your admin interface).

## Common tips & issues

- Accounts change servers when migrating. There may be a time of DNS propagations and it is necessary to update its `known_hosts` file for SSH connection. You can do this via the command (_[compte] to replace with the account name_):

```sh
$ ssh-keygen -R ssh-[compte].alwaysdata.net
```

- Drupal
  - [CSS and JS precompression](marketplace/drupal#précompression-des-fichiers-css) on the wrong versions of **8.9**.

- Segmentation vulnerabilities with [psycopg2](https://github.com/psycopg/psycopg2/issues/543).

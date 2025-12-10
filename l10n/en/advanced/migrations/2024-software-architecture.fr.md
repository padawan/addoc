+++
url = "/forward/migrations/software-architecture-2024/"
title = "Software Architecture 2024"
layout = "man"
hidden = true
tags = [ "infrastructure", "migration" ]
+++

## Major changes

- SSL is required for mail protocols (IMAP, SMTP, POP3) and remote access protocols (FTP, WebDAV).
- MongoDB and CouchDB databases are deleted.
- MariaDB is updated to version 10.11.
- PostgreSQL is updated to version 16.

## SSL encryption required for email access and remote access

It is necessary to enable SSL encryption to connect to protocols:

- of mail (IMAP, SMTP, POP3);
- remote access (FTP and WebDAV).

This does not affect your websites that are still accessible without encryption (however you can decide to [force encryption](security/ssl-tls/redirect-http-to-https/)).

### Supported TLS Versions

- TLS 1.2 and 1.3 versions are supported.
- TLS 1.0 and 1.1 versions are no longer supported.

This does not affect your websites for which you can always [configure the TLS yourself](security/ssl-tls/configure-tls/).

## MongoDB support stop

**MongoDB** switched to an [SSPL license](https://www.mongodb.com/licensing/server-side-public-license/faq) that also prohibits us from continuing to offer hosting MongoDB databases. As a result, MongoDB databases will be removed during migration and will no longer be possible to create them.

You can:

- run MongoDB yourself [in a service](guides/mongodb). _MongoDB will then no longer be managed by alwaysdata._ If you have a private cloud, we can help you achieve this result.
- migrate your databases to [MongoDB Atlas](https://www.mongodb.com/atlas).

## CouchDB support stop

We launched **CouchDB** support [in 2011](https://blog.alwaysdata.com/2011/05/12/official-support-of-couchdb/), but its use is kept confidential (less than 0.4% of our customers in 2024). As a result, we stop CouchDB support: the bases will be removed during the migration and it will not be possible to create one.

You can:

- run CouchDB yourself [in a service](guides/couchdb). _CouchDB will no longer be managed by alwaysdata._ If you have a private cloud, we can help you to realize this pattern.
- migrate your databases to a third-party host such as [Cloudant](https://www.ibm.com/products/cloudant).

## Update MariaDB

**MariaDB** is updated to [version 10.11](https://mariadb.com/kb/en/release-notes-mariadb-1011-series/).

You can check the update notes (your current version is listed in the _Databases > MySQL_ section):

- of [10.6 at 10.11](https://mariadb.com/kb/en/upgrading-from-mariadb-10-6-to-mariadb-10-11/);
- from [10.5 at 10.6](https://mariadb.com/docs/server/server-management/install-and-upgrade-mariadb/upgrading/upgrading-from-to-specific-versions/upgrading-from-mariadb-10-5-to-mariadb-10-6);
- of [10.4 at 10.5](https://mariadb.com/docs/server/server-management/install-and-upgrade-mariadb/upgrading/upgrading-from-to-specific-versions/upgrading-from-mariadb-10-4-to-mariadb-10-5).

## Updating PostgreSQL

**PostgreSQL** is updated to [version 16](https://www.postgresql.org/docs/16/release-16.html). You can check the [update notes](https://www.postgresql.org/docs/release/) (your current version is listed in the _Databases > PostgreSQL section_):

**PostGIS** is updated to [version 3.4](https://postgis.net/docs/manual-3.4/) (previously 3.1).

## Language Versions

### Switch to major versions

For [a few months] (https://changelog.alwaysdata.com/409/detail/), you can choose a major version of a language rather than a minor one. This allows you to automatically use the latest minor version available, with the latest patches.

The migration will automatically replace all selected versions with the corresponding major version. For example, PHP 8.3.1 will be replaced by PHP 8.3, which runs the latest version 8.3.x available. When a new version of PHP 8.3 is added, it will replace the previous version.

You will always have the option to select, after the migration, a minor version. It will then be this pre-release version that will run, without automatic update.

### Available versions

Here is the list of available minor versions:

| Language                | Available versions                                                                                                                                                                                                                                                                                                         |
| ----------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| PHP                     | `4.4.9` `5.2.17` `5.3.29` `5.4.45` `5.5.38` `5.6.40` `7.0.33` `7.1.33` `7.2.34` `7.3.33` `7.4.33` `8.0.30` `8.1.28` `8.2.19` `8.3.7`                                                                                                                                                                                       |
| Python                  | `2.4.6` `2.5.6` `2.6.9` `2.7.18` `3.3.7` `3.4.10` `3.5.10` `3.6.15` `3.7.17` `3.8.19` `3.9.19` `3.10.14` `3.11.9` `3.12.3`                                                                                                                                                                                                 |
| Ruby                    | `1.8.7-p374` `1.9.3-p551` `2.0.0-p648` `2.1.10` `2.2.2.10` `2.3.8` `2.4.10` `2.5.9` `2.6.10` \`\`2.7.8` `3.0.7` `3.1.6` `3.2.4` `3.3.3.2\` |
| Node.js | `6.17.1` `8.17.0` `10.24.1` `12.22.12` `14.21.3` `16.20.2` `18.20.3` `20.14.0`                                                                                                                                                                                                                                             |
| Elixir                  | `1.13.4` `1.14.5` `1.15.8` `1.16.3`                                                                                                                                                                                                                                                                                        |
| Java                    | `8.0.412` `11.0.23` `17.0.11` `21.0.3`                                                                                                                                                                                                                                                                                     |
| Deno                    | `1.43.5`                                                                                                                                                                                                                                                                                                                   |
| .NET    | `6.0.31` `8.0.6`                                                                                                                                                                                                                                                                                                           |

In particular, non-LTS versions of multiple languages have been removed:

- Node.js : 9, 11, 13, 15, 17, 19, 21
- Java: 14
- .NET: 5

If you used any of these releases, it will be replaced with the next major release.

## Various updates

The operating system changes from _Debian 10 (Buster)_ to _Debian 12 (Bookworm)_. As a result, numerous software and bibliothetics will be updated. Among notable updates:

- Erlang 25.2 (previously 21.2)
- GDAL 3.9 (previously 2.4)
- git 2.45 (previously 2.20)
- Go 1.22 (before 1.17)
- MapServer 8.0 (previously 7.4)
- PROJ 9.4 (before 5.2)
- QGIS 3.34 (formerly 3.4)
- RabbitMQ 3.10 (formerly 3.7)

### Private cloud

- **Redis**, if installed on your server, is updated to [version 7.0](https://github.com/redis/redis/blob/7.0/00-RELEASENOTES) (previously 6.0).

* **MySQL**, if installed on your server, is updated to [version 8.0](https://dev.mysql.com/doc/relnotes/mysql/8.0/en/).

- **Elasticsearch**, if installed on your server, is updated to version 8.17.

## Misc

- The `composer` command executes **Composer** 2. You can start Dial 1 with the `compose1` command.
- Default [HTTP Log Format](/sites/formatting-http-logs) becomes **Advanced**.
- **Transparent Redirect** sites are transformed into **Reverse Proxy**.
- IP 185.31.40.10 is an old IP address and will be deleted.

## Common tips & issues

- You can do yourself, _before migration_, some changes like selecting major versions of languages, use _Advanced_ log format or change your _Transparent Redirect_ sites.

- In [Public Cloud](accounts/billing/public-cloud-prices), your account will be moved to new servers during migration, so all services will change IP. The IPs used by each server are given in the **Advanced> Server Status** menu.
  - addresses of type `[service]-[compte].alwaysdata.net` may not be accessible from outside due to DNS propagation;
  - for domains not using our DNS servers, the previous HTTP server will redirect to the new HTTP server. Redirect may no longer work and it is appropriate to make IP changes to point to the correct server.

- It will be necessary to update your local `known_hosts` file to connect to SSH. You can do this via the command (_[compte] to replace with the account name_):

```sh
$ ssh-keygen -R ssh-[compte].alwaysdata.net
```

### Errors due to migration

1. `cannot open shared object file: No such file or directory`

Updating some system bibliotheques requires a recompilation of the code that uses them. The following bibliotheques are concerned:

- `libtiff`

In general, these libraries are not used directly by applications but by dependencies (PHP extension, Python module, Ruby gem, etc. ). Simply reinstall these dependencies on the new infrastructure to solve the problem.

## Why should migration be imposed?

The main purpose of the architecture migration is to upgrade our servers to a newer version of their operating system (Debian). It is important to proceed to these updates for two reasons:

- the security. Old software versions are not supported by their authors or distributors eternally. When a software stops supporting, it continues to work, but new security vulnerabilities are no longer fixed. Continuing to use these old versions would therefore run a risk for the security and reliability of your applications and data.

- to be able to use recent versions of software. The older an operating system is, the more difficult it is to run recent software. To continue offering you the latest versions of the software we offer (or that you can install yourself in your account), it is important to have a relatively recent version of the operating system.

These infrastructure migrations are carried out every four years. This corresponds to the hard life of a Debian release (from [five years](https://wiki.debian.org/LTS), but it is necessary to count the incompressible internal development time before switching to new versions). This seems to us to be a good balance, avoiding excessive migrations, but allowing to run the virtual totality of the recent software.

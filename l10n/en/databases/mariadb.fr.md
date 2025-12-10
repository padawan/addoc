+++
url = "/en/donation-bases/mariadb/"
title = "MariaDB / MySQL"
layout = "man"
tags = [ "database", "Mariadb", "mysql" ]
+++

## Login

|                   |                                                                                                                   |
| ----------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Server**        | mysql-[compte].alwaysdata.net |
| **Port**          | 3306 (default MySQL port)                                                                      |
| **Web interface** | [phpMyAdmin](https://phpmyadmin.alwaysdata.com/)                                                                  |

These login details depend on the account concerned. You can find the specific values in the **Databases > MySQL** section of the administration interface.

### Example with `mysql`

In our example, we use [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- Database name: `foo_base`
- We will use SSH and default database users that is, those created at the opening of accounts (i.e. `foo` for the _foo_ account).

```sh
foo@ssh:~$ mysql -h mysql-foo.alwaysdata.net -u foo -p foo_base
```

## Permissions

When creating your MySQL databases and users, you have the possibility to give the following permissions:

- all rights (GRANT ALL PRIVILEGES);
- read-only (GRANT READONLY);
- no rights.

{{% notice warning %}}
If you change the permissions of your users through a third-party app, any validation via the admin interface (or through the API) will reset the permissions according to the above directives.
{{%/notice %}}

## Restore a database from its daily backup

Multiple possibilities:

- use our [backup restore](backups/restore-a-site);

- use the following command:

    ```sh
    $ zstdcat $HOME/admin/backup/[date]/mysql/[base].sql.zst | mysql -h mysql-[compte].alwaysdata.net -u [utilisateur] -p [base]
    ```

- Retrieve the archive and use the client of his choice.

{{% notice tip %}}
Archived content (e.g. DB dumps in your _backup_ space are in [Zstandard]format (https://github.com/facebook/zstd), you can use the official [zstd\*\` tools](https://github.com/facebook/zstd/releases/latest) or the [plugin suitable for 7zip](https://www.tc4shell.com/en/7zip/modern7z/) to manipulate them.
{{%/notice %}}

## Misc

In Public Cloud, the maximum number of simultaneous connections per user is _40_. It is possible to modify it in Private Cloud.

MySQL blocks user names; if your account name is too large a _ID_ will be allocated to it. You can find it in **Databases > MySQL > Users**.

A [ANALYZE TABLE](https://mariadb.com/kb/en/analyze-table/) is executed daily on all your tables to ensure good performance, but please do not do this yourself when your data changes drastically, for example after a database import.

To know the MariaDB configuration, use the SQL `show variables` request.

_MySQL events_ are not supported on our Public Cloud.

On the Public Cloud you can change `sql_mode` to [connexion](https://dev.mysql.com/doc/refman/8.0/en/sql-mode.html) (SET SESSION).

{{% notice info %}}
MariaDB is offered by default on our servers but [Cloud Privacy](accounts/billing/private-cloud-prices) users may request to use MySQL.
{{%/notice %}}

---

- [MariaDB](https://mariadb.com/kb/en/library/documentation/)
- [MySQL documentation](https://dev.mysql.com/doc/)

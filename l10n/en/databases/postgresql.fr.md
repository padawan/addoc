+++
url = "/en/data-bases/postgresql/"
title = "PostgreSQL"
layout = "man"
tags = [ "database", "postgresql" ]
+++

## Login

|                   |                                                                                                                        |
| ----------------- | ---------------------------------------------------------------------------------------------------------------------- |
| **Server**        | postgresql-[compte].alwaysdata.net |
| **Port**          | 5432 (Default PostgreSQL Port)                                                                      |
| **Web interface** | [phpPgAdmin](https://phppgadmin.alwaysdata.com/)                                                                       |

These login details depend on the account concerned. You can find the specific values in the **Databases > PostgreSQL** section of the administration interface.

A _pgBouncer_ rotates on port `5433`. It is possible to connect to PostgreSQL instead of PostgreSQL directly.

### Example with `psql`

In our example, we use [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- Database name: `foo_base`
- We will use SSH and default database users that is, those created at the opening of accounts (i.e. `foo` for the _foo_ account).

```sh
foo@ssh:~$ psql -h postgresql-foo.alwaysdata.net -U foo -d foo_base
```

## Permissions

When creating your PostgreSQL databases and users, you define the permissions you want and our system performs the following steps:

- REVOKE ALL PRIVILEGES on the basis and its schemes;
- If your user should have **all rights**:
  - GRANT ALL PRIVILEGES on the basis and its schemes;
  - ALTER DEFAULT PRIVILEGES: GRANT ALL PRIVILEGES sur les TABLES, SEQUENCES et FUNCTIONS;
  - GRANT ALL PRIVILEGES sur les TABLES, SEQUENCES et FUNCTIONS.
- If your user should have **read-only** permission:
  - GRANT CONNECT on basis;
  - GRANT USAGE on schemes;
  - ALTER DEFAULT PRIVILEGES:
    - GRANT SELECT on TABLE, SEQUENCES;
    - GRANT EXECUTE on FUNCTIONS.
  - GRANT SELECT on TABLE, SEQUENCES;
  - GRANT EXECUTE on FUNCTIONS.

{{% notice warning %}}
If you change the permissions of your users through a third-party app, any validation via the admin interface (or through the API) will reset the permissions according to the above directives.
{{%/notice %}}

## Options

When creating a database, you have the following options:

- **local**: Determines the encoding, `LC_COLLATE` and `LC_CTYPE`;
- **extensions**: you can activate PostgreSQL extensions with a single click (`hstore`, `pgcrypto`, `PostGIS`, etc.). If you would like to use an unlisted extension, you can contact the [support](https://admin.alwaysdata.com/support/add/) to make it feel the need.

## Restore a database from its daily backup

Multiple possibilities:

- use our [backup restore](backups/restore-a-site);

- use the following command:

    ```sh
    $ zstdcat $HOME/admin/backup/[date]/postgresql/[base].sql.zst | psql -h postgresql-[compte].alwaysdata.net -U [utilisateur] -W -d [base]
    ```

- Retrieve the archive and use the client of his choice.

{{% notice tip %}}
Archived content (e.g. DB dumps in your _backup_ space are in [Zstandard]format (https://github.com/facebook/zstd), you can use the official [zstd\*\` tools](https://github.com/facebook/zstd/releases/latest) or the [plugin suitable for 7zip](https://www.tc4shell.com/en/7zip/modern7z/) to manipulate them.
{{%/notice %}}

## Misc

In Public Cloud, the maximum number of simultaneous connections per user is _50_. It is possible to modify it in [Private Cloud](accounts/billing/private-cloud-prices).

It is possible to see the names of all databases and users on PostgreSQL servers. This is a limitation of the use of PostgreSQL in a shared environment. The contents of the bases are **not** accessible.

PostgreSQL _untrusted_ languages, allowing to execute arbitrary code under the rights of the administrator user (running PostgreSQL), cannot be used on our servers.

---

- [PostgreSQL documentation](https://www.postgresql.org/docs/)

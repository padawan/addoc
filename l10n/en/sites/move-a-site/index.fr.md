+++
url = "/sites/moplacer-un-site/"
title = "How to move a website"
layout = "howto"
hidden = true
tags = [ "site" ]
+++

This article explains how to move a site to another alwaysdata account.

To do so, we will use [SSH access](remote-access/ssh) rather than FTP which requires to fetch files locally and then transfer them to the destination account.

In our example, we will be able to use the following information:

- Original account name: `foo`
- Destination account name: `bar`
- Original Database Name: `foo_base`
- Destination database name: `bar_base`
- The site is located in the `$HOME/www/` directory
- We will use SSH and default database users i.e. those created at the opening of accounts (e.g. `foo` for the _foo_ account and `bar` for the _bar_ account).

## 1. Copying files

We use the command [scp](https://linux.die.net/man/1/scp) after connecting in SSH to the account of **destination**.

```sh
bar@ssh:~$ scp -r foo@ssh-foo.alwaysdata.net:/home/foo/www/* ~/www/
```

## 2. Database import

This step is only necessary if your site is connected to a database.

If both accounts use the same RDBMS version and belong to the same profile, you can use our function of [database duplication](databases/duplicate-database).

Alternatively, you can do this manually by creating the database on the _destination_ account and then running the following commands:

- MySQL :

```sh
bar@ssh:~$ mysqldump -u foo -p -h mysql-foo.alwaysdata.net foo_base > foo_base.sql
bar@ssh:~$ mysql -h mysql-bar.alwaysdata.net -u bar -p bar_base < foo_base.sql
bar@ssh:~$ rm foo_base.sql
```

- PostgreSQL:

```sh
bar@ssh:~$ pg_dump -U foo -W -h postgresql-foo.alwaysdata.net foo_base > foo_base.sql
bar@ssh:~$ psql -h postgresql-bar. lwaysdata.net -U bar -W -d bar_base < foo_base.sql
bar@ssh:~$ rm foo_base.sql
```

{{% notice info %}}
In both cases, you will need to modify the previously copied site configuration file to point to the newly imported base.
{{%/notice %}}

## 3. Moving addresses

{{% notice info %}}
Only the _account owner_ can initiate the assignment.
{{%/notice %}}

You have to move the addresses attached to the site and their self-managed SSL certificate.

1. Go to the **Web > Sites** section of the original account;
2. {{< fig "images/admin-panel_move-website-1.en.png" "Admin interface: site move - step 1" >}}
3. {{< fig "images/admin-panel_move-website-2.en.png" "Admin interface: site move - step 2" >}}

WARNING: For sites using a command[^1], the site can see its port changed.

{{% notice info %}}
An address in `.alwaysdata.net` cannot be linked to the account name.
{{%/notice %}}

{{% notice tip %}}
To move it to another of _ses_ accounts there is only to specify its own email address.
{{%/notice %}}

[^1]: Node.js, User Program, Elixir and Deno types.

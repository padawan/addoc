+++
url = "/savegardes/restaurer-un-site/"
title = "How to restore a website"
linkTitle = "Restore Site"
layout = "howto"
weight = 5
tags = [ "database", "start", "backup", "site" ]
+++

The backups of your files and databases can be found in your account's `$HOME/admin/backup` directory. You can restore them via the **Advanced> Backup restore** menu.

1. Choose the desired date;
   {{< fig "images/admin-panel_restoration.en.png" "Administration interface: restore backup - step 1" >}}

2. Then check the database(s) and/or the desired directory(s) [^1].  
   {{< fig "images/admin-panel\_restoration-site.png" "Admin interface: restore backup - step 2" >}}

{{% notice warning %}}
Restore will overwrite the current configuration, so make a backup first.
{{%/notice %}}

{{% notice note %}}
Restore time depends on file size to restore.
{{%/notice %}}

## In SSH

If you want to restore a backup manually.

- Log in to your [SSH](remote-access/ssh);

- Restore files:

    ```sh
    $ rsync -av --delete $HOME/admin/backup/[date]/files/[répertoire]/ $HOME/[répertoire]/
    ```

{{% notice warning %}}
`--delete` will delete all files in this directory that have been created since the backup date.
To perform a test add `-n`.
{{%/notice %}}

- Restore MySQL database:

    ```sh
    $ zstdcat $HOME/admin/backup/[date]/mysql/[base].sql.zst | mysql -h mysql-[compte].alwaysdata.net -u [utilisateur] -p [base]
    ```

- Restore PostgreSQL database:

    ```sh
    $ zstdcat $HOME/admin/backup/[date]/postgresql/[base].sql.zst | psql -h postgresql-[compte].alwaysdata.net -U [utilisateur] -W -d [base]
    ```

{{% notice tip %}}
Archived content (e.g. DB dumps in your _backup_ space are in [Zstandard]format (https://github.com/facebook/zstd), you can use the official [zstd\*\` tools](https://github.com/facebook/zstd/releases/latest) or the [plugin suitable for 7zip](https://www.tc4shell.com/en/7zip/modern7z/) to manipulate them.
{{%/notice %}}

[^1]: It is not mandatory to restore both databases and files.

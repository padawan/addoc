+++
url = "/savegardes/restaurer-des-emails/"
title = "How to restore emails"
linkTitle = "Restore emails"
layout = "howto"
weight = 10
tags = [ "email", "start", "backup" ]
+++

Your email backups can be found in your account's `$HOME/admin/backup` directory. You can restore them via the **Advanced> Backup restore** menu.

{{% notice info %}}
Emails on the backup date will be restored. No emails received or sent since will be deleted.
{{%/notice %}}

1. Choose the desired date;
   {{< fig "images/admin-panel_restoration.en.png" "Administration interface: restore backup - step 1" >}}

2. Then check the email(s).  
   {{< fig "images/admin-panel_restoration-emails.en.png" "Admin interface: restore backup - step 2" >}}

{{% notice note %}}
Restore time depends on file size to restore.
{{%/notice %}}

## In SSH

If you want to restore a backup manually.

- Log in to your [SSH](remote-access/ssh);

- Restore Emails:

    ```sh
    $ rsync -av $HOME/admin/backup/[date]/mails/[domaine]/[boîte_email]/ $HOME/admin/mail/[domaine]/[boîte_email]/
    ```

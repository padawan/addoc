+++
url = "/en/backups"
title = "Backups"
pre = "<i class='fas fa-fw fa-history'></i> "
weight = 34
archetype = "chapter"
tags = [ "start", "backup" ]
+++

A backup of your files, databases and emails is performed **daily** and available in your account's `$HOME/admin/backup` directory. These backups are kept for a number of _slipper_ days, depending on the plan chosen:

| Public Cloud |        |         |         |         | Private Cloud     |              |
| ------------ | ------ | ------- | ------- | ------- | ----------------- | ------------ |
| Free         | Small  | Medium  | Wide    | X-Large | Servers dedicated | Gold Servers |
| 3 days       | 7 days | 20 days | 20 days | 30 days | 30 days           | 30 days      |

Regardless of the offer taken, backups are stored in a data center, several kilometres away from the production center and using another provider.

You can restore [a website](restore-a-site) or [emails](restore-e-mails) in the **Advanced> Backup restore** tab of your admin interface.

{{% notice info %}}
Backups do not count into an account's disk space quota.
{{%/notice %}}

{{% notice tip %}}
Archived content (e.g. DB dumps in your _backup_ space are in [Zstandard]format (https://github.com/facebook/zstd), you can use the official [zstd\*\` tools](https://github.com/facebook/zstd/releases/latest) or the [plugin suitable for 7zip](https://www.tc4shell.com/en/7zip/modern7z/) to manipulate them.
{{%/notice %}}

- [Alwaysdata Activity Continuity Plan](security/drp)

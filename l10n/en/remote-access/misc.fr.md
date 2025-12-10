+++
url = "/remote/diverse/"
title = "Various questions"
layout = "faq"
hidden = true
tags = [ "account", "technical environment" ]
+++

## List Accounts

The list of alwaysdata accounts is visible in several ways. Their contents are NOT accessible, however.

## `/tmp` directory

The `/tmp` directory is a directory shared by all users on a server. It is not recommended to use it and, by default, files are readable by other users. `$HOME/admin/tmp` is preferred, having the same isolation as the rest of the directories of an account.

## Disk space quota

Backups (`$HOME/admin/backup`) like most logs (`$HOME/admin/logs`) do not count into disk space quota.

Only the _apache_, _php_ and _uwsgi_ logs of the current month are included in an account's disk space quota.

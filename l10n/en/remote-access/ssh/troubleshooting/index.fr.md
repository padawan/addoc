+++
url = "/remote-access/ssh/frequent-issues/"
title = "SSH - Frequent Issues"
layout = "faq"
weight = 70
hidden = true
tags = [ "remote access", "troubleshooting", "ssh" ]
+++

## Login

When connecting problems you can use the `ssh -v [utilisateur]@ssh-[compte].alwaysdata.net` command for more information.

{{% notice note %}}
Replace `[utilisateur]` with your SSH username and `ssh-[compte].alwaysdata.net` with your SSH host-name.
{{%/notice %}}

A [IP block] (security/network#prévention-des-intrusions) occurs after about ten failed attempts to connect to the server.

{{% notice info %}}
alwaysdata has login logs from which you can exceptionally request a copy.
{{%/notice %}}

### Too many authentication failures

This is an SSH key issue, please specify the corresponding key. If you can't find it, log in by password and update the `$HOME/.ssh/authorized_keys` file.

### WARNING: HOST REMOTE IDENTIFICATION HAS CHANGED!

An account can be moved from an SSH server. New fingerprints are specified in **Remote Access > SSH**.

It is necessary to update the `known_hosts` file, which is possible via the following command:

```ssh
$ ssh-keygen -R [host_name]
```

### Input/output error

Error linked to opeditions from our side, wait for it to finish but you can also contact the [support](https://admin.alwaysdata.com/support/add/) for more information.

## Permissions

Using multiple SSH users may have undesirable side effects: errors when accessing certain files, deleting folders...

If so, you can:

- remove problem SSH user. This automatically reassigns the files it owned to the primary user.
- use the `chmod` command with the owner user of the affected files to give the necessary group permissions.

{{% notice warning %}}
Processes started by a site (**Web > Sites**), typically _Apache_ or _PHP_, run with the primary user.
{{%/notice %}}


+++
url = "/remote-access/ssh/"
title = "SSH"
weight = 5
tags = [ "remote access", "ssh" ]
archetype = "chapter"
+++

SSH, for [Secure Shell](https://fr.wikipedia.org/wiki/Secure_Shell), is a connection protocol secured by an initial connection exchange of encryption keys. alwaysdata offers it on ALL its environments.

**Remote SSH access is disabled by default.** To enable it, change your user and check password login. It is then possible to set up a connection by [SSH keys](use-keys) and disable password login.

- [API - SSH](https://api.alwaysdata.com/v1/ssh/doc/)
- [Create SSH user](create-a-ssh-user)
- [Freight issues](remote-access/ssh/troubleshooting)

* [Private Cloud] Users (accounts/billing/private-cloud-prices):
  - [SSH 2-factor authentication](remote-access/ssh/ssh-two-factor-authentication)
  - [Global SSH Keys](install-globally-ssh-keys)

{{% notice info %}}
All our offers are info, it is not possible to have a `root` access.
{{%/notice %}}

## Connect in SSH

| Information |                                                                                                                 |
| ----------- | --------------------------------------------------------------------------------------------------------------- |
| Hostels     | ssh-[compte].alwaysdata.net |
| Ports       | 22                                                                                                              |
| Username    | associated user and password OR SSH keys                                                                        |

{{< fig "admin-panel_ssh-users-list.en.png" "Admin interface: list of SSH users" >}}

### By a terminal

Open your terminal and type the following command:

```ssh
$ ssh [utilisateur]@ssh-[compte].alwaysdata.net
```

{{% notice note %}}
Replace `[utilisateur]` with your SSH username and `ssh-[compte].alwaysdata.net` with your SSH host-name.
{{%/notice %}}

### Web

Useful if you are behind a firewall, our [web interface](https://tsl0922.github.io/ttyd/) allows you to use SSH from your browser. To use it, type `https://ssh-[compte].alwaysdata.net` in your web browser's address bar.

Warning, this unreliable and slow solution does not replace an SSH client.

{{% notice info %}}
This interface is not compatible with [Private Cloud](accounts/billing/private-cloud-prices).
{{%/notice %}}

## Misc

The _fingerprints_ of our SSH servers are displayed in the **Remote Access > SSH** tab of your admin interface.

Ongoing processes can be accessed via the **Advanced> Process > SSH** menu.

SSH users are not `chroot`. Even if the root directory of the user is not the root directory of the account, he will be able to access the entire account.

---

- [OpenSSH](https://www.openssh.com/);
- [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/download.html) : SSH terminal on Windows.

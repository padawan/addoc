+++
url = "/remote-access/ssh/use keys-ssh/"
title = "How to use SSH keys"
layout = "howto"
weight = 20
hidden = true
tags = [ "remote access", "ssh" ]
+++

Connecting in SSH with its public key (with or disabling password login) provides some benefits: enhanced security, Possibility of defining an "empty" password, etc. Here are the steps to configure your SSH account with public key.

{{% notice note %}}
SSH access is **disabled by default**. You will need to enable password login at least temporarily to add SSH keys.
{{%/notice %}}

## On Windows

The manipulations are performed thanks to _PuTTY_, an SSH client [available for free](https://www.chiark.greenend.org.uk/~sgtatham/putty/download.html).

1. Manage private key:
   - Launch **PuTTYGen** (provided by PuTTy);
   - Geek a **SSH-2 ED25519** keypair;
   - Save the private key on your position;
2. Report the key on the server by copying this key to the `$HOME/.ssh/authorized_keys` file of your alwaysdata account;
3. Set up your **PuTTY** session to connect to SSH:
   - Go to the **SSH > Auth** menu, to enter the path to your private key in _Private Key file for authentication_.

## Under Unix / OS X

1. Generate Keys:

```sh
$ mkdir -p $HOME/.ssh
$ chmod 0700 $HOME/.ssh
$ ssh-keygen -t ed25519 -f $HOME/.ssh/id_ed25519
```

{{% notice tip %}}
If you want to never have to enter your password when you login in SSH, specify an empty passphrase.
{{%/notice %}}

2. Declare public key (.pub) on server:

```sh
$ ssh-copy-id -i $HOME/.ssh/id_ed25519.pub [utilisateur]@ssh-[compte].alwaysdata.net
```

Or by copying the contents of this file to the `$HOME/.ssh/authorized_keys` file in your alwaysdata account.

{{% notice note %}}
Replace `[utilisateur]` with your SSH username and `ssh-[compte].alwaysdata.net` with your SSH host-name.
{{%/notice %}}

[Private Cloud] (accounts/billing/choose-its-paas) users can declare them [directly in the admin interface](remote-access/ssh/install-globally-ssh-keys), they will then be global to the server and therefore usable to all accounts.

3. Connect in SSH: At the next SSH connection, your passphrase will be asked (or nothing if your passphrase is empty).

{{% notice info %}}
DSA keys are [not accepted](https://www.openssh.com/legacy.html).
{{%/notice %}}

+++
url = "/guides/tideways/"
title = "How to install Tideways"
layout = "howto"
hidden = true
tags = [ "http", "monitoring", "profile" ]
+++

[Tideways](https://tideways.com/) monitors PHP applications and helps optimize them. Due to the special features of our infrastructure, their installation script is not usable on our servers, here are the steps to follow.

In our example, we use a [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- Tideways directory: `$HOME/tideways/`

{{% notice note %}}
`[foo]`, `[version]` and `[php_version]` must be replaced with the correct information.
{{%/notice %}}

## Step 1: Downloading agent and daemon

```sh
foo@ssh:~/tideways$ wget -O- https://s3-eu-west-1.<unk> tideways/extension/[version]/tideways-php-[version]-x86_64.tar.gz | tar -xz --strip-components=1
foo@ssh:~/tideways$ wget -O- https://s3-eu-west-1.<unk> tideways/daemon/[version]/tideways-daemon_linux_amd64-[version].tar.gz | tar -xz --strip-components=0
```

[Download page](https://tideways.io/profiler/downloads)

## Step 2: Modifying php.ini

Add to the `php.ini` (**Environment > PHP** or **Web > Sites > Edit [site] - ⚙️ > Configuration**):

```ini
extension = /home/[foo]/tideways/tideways-[version]/tideways-php-[php-version].so
```

[Configuration documentation](https://support.tideways.com/documentation/setup/configuration)

## Step 3: Launching daemon

```sh
foo@ssh:~/tideways$ chmod +x tideways-daemon_[version]/tideways-daemon
```

Create an [service](services) with the following details:

- _Command_: `/home/[foo]/tideways/tideways-daemon_[version]/tideways-daemon -address /home/[foo]/tideways/tidewaysd.sock`
- _Work directory_: `/home/[foo]/tideways/tideways-daemon_[version]/`

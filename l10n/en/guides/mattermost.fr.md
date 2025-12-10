+++
url = "/guides/mattermost/"
title = "How to install Mattermost"
layout = "howto"
hidden = true
+++

[Mattermost](https://mattermost.com) is an instant messaging software.

In our example, we use a [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- Mattermost directory: `$HOME/mattermost/`
- PostgreSQL database: `foo_mattermost` - created in the **Databases > PostgreSQL** menu of [the administration interface](https://admin.alwaysdata.com)
- Port: 8300 (ports between 8300 and 8499 can be used)

{{% notice note %}}
`[foo]` and `[version]` must be replaced with the correct information.
{{%/notice %}}

## Setup

```sh
foo@ssh:~/mattermost$ wget -O- https://releases.mattermost.com/[version]/mattermost-[version]-linux-amd64.tar.gz | tar -xz --strip-components=1
foo@ssh:~/mattermost$ mkdir data
```

[Download page](https://mattermost.com/deploy/)

## Setup

A database and its user will have to be created in the **Databases** menu. Here we create them to be of the `account_mattermost` form.

Edit the `$HOME/mattermost/config/config.json` file to say:

```txt
"ListenAddress": ":8300",
"LocalModeSocketLocation": "$HOME/admin/tmp/mattermost_local.socket",
```

- PostgreSQL

```txt
"DriverName": "postgres",
"DataSource": "postgres://[foo]_mattermost:[motdepasse_pgsql]@postgresql-[foo].alwaysdata.net:5432/[foo]_mattermost?sslmode=disable\u0026connect_timeout=10",
```

## Launching service

Create an [service](services) with the following details:

- _Command_: `/home/[foo]/mattermost/bin/mattermost`
- _Work directory_: `/home/[foo]/mattermost`

## Site creation

Make an [site](sites/add-a-site) of type **Reverse proxy** with:

- _Remote URL_: `services-[foo].alwaysdata.net:8300`

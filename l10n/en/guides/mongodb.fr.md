+++
url = "/guides/mongodb/"
title = "MongoDB"
layout = "howto"
hidden = true
tags = [ "database", "Mongodb" ]
+++

[MongoDB](https://www.mongodb.com/) is a noSQL RDBMS oriented documents.

In our example, we use a [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- MongoDB directory: `$HOME/mongodb/`

{{% notice note %}}
`[foo]` is to replace with the name of your account.
{{%/notice %}}

## Setup

### Download

```sh
foo@ssh:~$ mkdir mongodb
foo@ssh:~$ cd mongodb
foo@ssh:~/mongodb$ wget -O- https://fastdl.mongodb.org/linux/mongodb-linux-x86_64-debian12-8.0.1.tgz | tar -xz --strip-components=1
foo@ssh:~/mongodb$ mkdir -p data log
```

Choose the _tgz_ package and _Debian_ platform of the [latest tarball version](https://www.mongodb.com/try/download/community).

### Launching service

Create an [service](services) with the following details:

- _Command_: `./bin/mongod --dbpath ./data/ --logpath ./log/mongo.log --ipv6 --bind_ip_all --port=27017`
- _Work directory_: `/home/[foo]/mongodb`

[Public Cloud](accounts/billing/public-cloud-prices) users will need to point the service to a port between 8300 and 8499 instead of the default port of MongoDB.

The address to connect to the MongoDB instance will be `services-[foo].alwaysdata.net:[port]`.

{{% notice note %}}
Replace `[port]` with the chosen port at command level.
{{%/notice %}}

### Creation of Firewall

[Private Cloud] (accounts/billing/private-cloud-prices) users will have to open the port they use by creating a replica on the [parefeu](security/network/configure-firewall) if they wish to access it from the outset:

| Featured                        | Value                |
| ------------------------------- | -------------------- |
| Order set                       | UDP/TCP              |
| SMESH_TYPE | ACCEPT               |
| Direction                       | Company              |
| Hosts                           | \<ne rien indiquer> |
| Ports                           | 27017                |
| IP Version                      | IPv4/IPv6            |

## Downloading and installing utilities

- [mongosh](https://www.mongodb.com/try/download/shell) - choose the _tgz_ package and the _Linux x64_ platform of the latest version.

```sh
foo@ssh:~/mongodb$ wget -O- https://downloads.mongodb.com/compass/mongosh-2.3.2-linux-x64.tgz | tar -xz --strip-components=0
foo@ssh:~/mongodb$ mv mongosh-2.3.2-linux-x64/bin/* bin/
foo@ssh:~/mongodb$ rm -rf mongosh-2.3.2-linux-x64
```

- [cli](https://www.mongodb.com/try/download/database-tools) - choose the _tgz_ package and the _Debian 12.0 x86-64_ platform of the latest version.

```sh
foo@ssh:~/mongodb$ wget -O- https://fastdl.mongodb.org/tools/db/mongodb-database-tools-debian12-x86_64-100.10.0.tgz | tar -xz --strip-components=0
foo@ssh:~/mongodb$ mv mongodb-database-tools-debian12-x86_64-100.10.0/bin/* bin/
foo@ssh:~/mongodb$ rm -rf mongodb-database-tools-debian12-x86_64-100.10.0
```

All executables will thus be in `$HOME/mongodb/bin`.

## Authentication

Here we will create the user _admin_ by following [their documentation](https://www.mongodb.com/docs/manual/tutorial/configure-scram-client-authentication/#create-the-user-administrator).

```sh
foo@ssh: ~/mongodb$ ./bin/mongosh services-[foo].alwaysdata.net:[port]
Current Mongosh Log ID:6707c8c098d8f59e6efe6910
Connecting to:mongodb://services-[foo].alwaysdata. and:[port]/?directConnection=true&appName=mongosh+2.3.2
Using MongoDB: 8.0.1
Using Mongosh:2.3.2

------

test> use admin
switched to db admin
admin> db. reateUser(
... {
... user: "admin",
... pwd: "mysuperpassword",
. . roles: [
... { role: "userAdminAnyDatabase", db: "admin" },
. { role: "readWriteAnyDatabase", db: "admin" }
... ]
. . }
... )
{ ok: 1 }
admin>
```

{{% notice note %}}
`mysuperpassword` is to be replaced with the password of your choice.
{{%/notice %}}

You can then add the `--auth` option to the command of the [service](#lancement-du-service).

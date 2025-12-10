+++
url = "/guides/couchdb/"
title = "LayDB"
layout = "howto"
hidden = true
tags = [ "database", "bedding" ]
+++

[CouchDB](https://couchdb.apache.org/) is a noSQL RDBMS oriented documents.

In our example, we use a [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- LayDB directory: `$HOME/couchdb/`

{{% notice note %}}
`[foo]` must be replaced by the name of your account.
{{%/notice %}}

## Setup

### Download and compile

```sh
foo@ssh:~$ mkdir couchdb
foo@ssh:~$ cd couchdb
foo@ssh:~/couchdb$ wget -O- https://dlcdn.apache.org/couchdb/source/3.4.1/apache-couchdb-3.4.1.tar.gz | tar -xz --strip-components=1
foo@ssh:~/couchdb$ ./configure --spidermonkey-version 78
foo@ssh:~/couchdb$ make release
```

Choose the _tar.gz_ package of the latest version available on [the CouchDB institutional site](https://dlcdn.apache.org/couchdb/source/).

### Setup

Create a `local.ini` file in the `$HOME/couchdb` directory with the following directives:

```
[admins]
admin = mysuperpassword

[couchdb]
single_node = true

[chttpd]
bind_address = ::
port = 5984
```

{{% notice note %}}
`mysuperpassword` is to be replaced with the password of your choice.
{{%/notice %}}

Users of [Public Cloud] (accounts/billing/public-cloud-prices) will need to point the service to a port between 8300 and 8499 and change this value in the configuration file.

### Launching service

Create an [service](services) with the following details:

- _Command_: `./bin/couchdb -couch_ini /home/[foo]/couchdb/local.ini`
- _Work directory_: `/home/[foo]/couchdb/rel/couchdb`

The address to connect to the CouchDB instance will be `services-[foo].alwaysdata.net:[port]`. For example, to list databases:

```
$ curl -X GET http://admin:mysuperpasswordpass@services-[foo].alwaysdata.net:[port]/_all_dbs
```

{{% notice note %}}
`[port]` is to be replaced by the port specified in the `local.ini` file.
{{%/notice %}}

### Creation of Firewall

[Private Cloud] (accounts/billing/private-cloud-prices) users will have to open the port they use by creating a replica on the [parefeu](security/network/configure-firewall) if they wish to access it from the outset:

| Featured                        | Value                |
| ------------------------------- | -------------------- |
| Order set                       | UDP/TCP              |
| SMESH_TYPE | ACCEPT               |
| Direction                       | Company              |
| Hosts                           | \<ne rien indiquer> |
| Ports                           | 5984                 |
| IP Version                      | IPv4/IPv6            |

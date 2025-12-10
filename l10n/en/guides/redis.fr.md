+++
url = "/guides/redis/"
title = "Redis"
layout = "howto"
hidden = true
tags = [ "http", "Redis", "site" ]
+++

[Redis](https://redis.io/) is an expandable key value data base management system.

Here is an installation guide on [Cloud Public](accounts/billing/public-cloud-prices). [Private Cloud] (accounts/billing/private-cloud-prices) users can request the installation of _Redis_ [at server level](databases/redis).

In our example, we use a [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- Redis directory: `$HOME/redis/`
- Port: 8300 (ports between 8300 and 8499 can be used)

{{% notice note %}}
`[foo]` must be replaced with the correct account name.
{{%/notice %}}

## Setup

### Download and compile

```sh
foo@ssh:~/redis$ wget -O- https://download.redis.io/redis-stable.tar.gz | tar -xz --strip-components=1
foo@ssh:~/redis$ make
```

### Launching service

Create the following [service](services) :

- _Command_: `./src/redis-server --bind :: --port 8300 --protected-mode no`
- _Control monitoring_: `./src/redis-cli redis.conf -h services-[foo].alwaysdata.net -p 8300 ping`
- _Work directory_ : `/home/[foo]/redis`

More options via `$HOME/redis/src/redis-cli -h`.

Then it will remain the configuration of the application that to connect to Redis will have to use `services-[foo].alwaysdata.net` and port `8300`.

- [Install PHP extension](databases/redis/php)

## Authentication

By default anyone can connect to Redis; there is no security. Une [authentification](https://redis.io/docs/management/security/acl/) peut donc être mise en place.

You will need to create the `users.acl` file and change the `aclfile` line in the Redis `redis.conf` configuration file.

In the following example, we will specify a password (`[password]`) to the user by default.

```sh
foo@ssh:~/redis$ ./src/redis-cli -h services-[foo].alwaysdata.net -p 8300
services-[foo].alwaysdata. and:8300> ACL LIST
1) "user default on nopass sanitize-payload ~* &* +@all"

services -[foo]. lwaysdata.net:8300> ACL SETUSER default on >[password]

services -[foo].alwaysdata. and:8300> ACL LIST
1) "user default on sanitize-payload #1ccc91f99d0c4c7a24e77941b18c0339ecb3eaf5ad7ae9ad816a7e69d83b69db ~* &* +@all"

services-[foo].alwaysdata. and:8300> ACL SAVE
OK

services-[foo].alwaysdata.net:8300> CONFIG REWRITE
OK

services-[foo].alwaysdata.net:8300> AUTH default [password]
OK
```

- [`ACL LIST`](https://redis.io/commands/acl-list/) lists users and gives information about user rights.
- [`ACL SETUSER`](https://redis.io/commands/acl-setuser/) creates or modifies users.
- [`ACL SAVE`](https://redis.io/commands/acl-save/) saves users.

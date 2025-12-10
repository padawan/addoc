+++
url = "/guides/memcached/"
title = "How to install Memcached"
layout = "howto"
hidden = true
tags = [ "cache", "http", "memcached", "site" ]
+++

[Memcached](https://www.memcached.org/) is an object oriented cache engine.

Here's an installation guide on the Public Cloud.

{{% notice info %}}
_Memcached_ can be [installed at server level](databases/memcached) for Private Cloud users.
{{%/notice %}}

In our example, we use a [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- Memcached directory: `$HOME/memcached/`
- Port: 8300 (ports between 8300 and 8499 can be used)

{{% notice note %}}
`[foo]` must be replaced with the correct account name.
{{%/notice %}}

## Step 1: Installation

```sh
foo@ssh:~/memcached$ wget -O- http://memcached.org/latest| tar -xz --strip-components=1
foo@ssh:~/memcached$ ./configure && make
```

## Step 2: Launching the service

Create the following [service](services) :

- _Command_: `./memcached -p 8300`
- _Work directory_: `/home/[foo]/memcached`

More options via `$HOME/memcached/memcached -h`.

{{% notice warning %}}
By default, anyone can connect to Memcached ; there is no security at all. An [authentification](https://github.com/memcached/memcached/wiki/SASLHowto) can be set up.
{{%/notice %}}

Then it will remain the configuration of the application that to connect to the Memcached will have to use `services-[foo].alwaysdata.net` and port `8300`.

- [Install PHP extension](databases/memcached/php)

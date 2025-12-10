+++
url = "/guides/new-relic/"
title = "How to install New Relic"
layout = "howto"
hidden = true
tags = [ "http", "monitoring", "site" ]
+++

[New Relic](https://newrelic.com/products/application-monitoring) monitors applications and helps optimize them. It offers agents in several languages and we will present here the steps to install **PHP and Python agents**.

In our example, we use a [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`

{{% notice note %}}
`[foo]`, `[newrelic-last-version]`, `[version]` and `REPLACE_WITH_LICENSE_KEY` must be replaced with the correct information.
{{%/notice %}}

## PHP

Due to the special features of our infrastructure, their installation script is not usable on our servers, here are the steps to follow.

- New Relic Directory: `$HOME/newrelic/`

### Private Cloud

#### Step 1: Agent's Download

```sh
foo@ssh:~/newrelic$ wget -O- https://download.newrelic.com/php_agent/release/[newrelic-last-version]-linux.tar.gz | tar -xz --strip-components=1
```

[Download page](https://download.newrelic.com/php_agent/release/)

#### Step 2: Modifying php.ini

Add to the `php.ini` (**Environment > PHP**):

```ini
extension = /home/[foo]/newrelic/agent/x64/newrelic-[version].so
newrelic.license = "REPLACE_WITH_LICENSE_KEY"
newrelic.enabled = true
newrelic.loglevel = "info"
newrelic.logfile = "/home/[foo]/newrelic/php_agent.log"
```

More options are available in `/home/[foo]/newrelic/scripts/newrelic.ini.template`.

#### Step 3: Launching daemon

Create an [service](services) with the following details:

- _Command_: `/home/[foo]/newrelic/daemon/newrelic-daemon.x64 -f --logfile /home/[foo]/newrelic/daemon/log`
- _Work directory_: `/home/[foo]/newrelic`

### Public Cloud

#### Step 1: Agent's Download

```sh
foo@ssh:~/newrelic$ wget -O- https://download.newrelic.com/php_agent/release/[newrelic-last-version]-linux.tar.gz | tar -xz --strip-components=1
```

[Download page](https://download.newrelic.com/php_agent/release/)

#### Step 2: Modifying php.ini

Add to the `php.ini` (**Environment > PHP**):

```ini
extension = /home/[foo]/newrelic/agent/x64/newrelic-[version].so
newrelic.license = "REPLACE_WITH_LICENSE_KEY"
newrelic.enabled = true
newrelic. oglevel = "info"
newrelic.logfile = "/home/[foo]/newrelic/php_agent.log"
newrelic.daemon.location="/home/[foo]/newrelic/daemon/newrelic-daemon.x64"
```

More options are available in `/home/[foo]/newrelic/scripts/newrelic.ini.template`.

## Python

New Relic is a Python module to install like any other. If the app uses a `virtualenv`, New Relic will be installed at the `virtualenv` level.

### Step 1: Agent Installation

```sh
foo@ssh:~$ python -m pip install newrelic
foo@ssh:~$ newrelic-admin generate-config REPLACE_WITH_LICENSE_KEY newrelic.ini
```

### Step 2: Changing application configuration

Add to the app's `.py` file:

```txt
import newrelic.agent
newrelic.agent.initialize('/home/[foo]/newrelic.ini')
```

---

## Links

- [Documentation](https://docs.newrelic.com/docs/new-relic-solutions/new-relic-one/install-configure/configure-new-relic-agents/#apm-config)

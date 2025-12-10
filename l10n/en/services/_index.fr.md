+++
url = "/services/"
title = "Services"
pre = "<i class='fas fa-fw fa-sitemap'></i> "
weight = 33
layout = "man"
tags = [ "services" ]
+++

You can define services, that is, geometric programs that run 24 hours a day without any useful interaction. Contrary to a command manually launched in SSH, these services will be relaunched automatically by the system in case of stopping.

These services are controlled via the **Advanced> Services** menu of the [Administration Interface](https://admin.alwaysdata.com).

{{< fig "admin-panel_create-service.png" "" >}}

ports `8300` at `8499` and host name `services-[compte].alwaysdata.net`[^1] can be used to run these services.

- [API Reference](https://api.alwaysdata.com/v1/service/doc/)

## Use services

- It must stay ahead (`foreground`) and not forker and leave [^2];
- If it wants to listen on a port it must be attached to _IPv6_ on `::` and listen a port between `8300` and `8499`;
- A log is automatically created and available in the `$HOME/admin/logs/services/` directory. It gives you the start and stop of the service.
  - An excerpt of these logs is present in the alwaysdata admin interface (**Logs** - 📄).
- Ongoing processes can be accessed via the **Advanced> Process > Services** menu;
- Restarting a service returns the `SIGHUP` signal;
- If a service fails several times in a short time, it will be automatically disabled;
- The language versions used by default are those specified in the **Environment** menu of the admin interface. It is possible to choose another version using _Environment Variables_.

The _Control Monitoring_ field — optional — specifies a command that makes sure the service is functional. When this command returns an error code, the service is restarted. It may, for example, check that the service is well reachable on the port assigned to it (e.g. for a service using port _8300_):

```sh
$ nc -z services-[compte].alwaysdata.net 8300
```

{{% notice warning %}}
There is no network filtering, anyone can connect to your services. Make sure your services have an authentication mechanism if necessary.
{{%/notice %}}

For [Public Cloud](accounts/billing/public-cloud-prices) users:

- Services are executed on separate servers from SSH and HTTP;
- Consumption must remain reasonable;
- Services will not be reachable via IPv4, only IPv6.

For [Private Cloud] (accounts/billing/private-cloud-prices) users:

- The ports `8300` at `8499` are _not_ open to the outside. It is possible to open them via a [firewall real](security/network/configure-firewall);
- You can use other ports, for example the default port of the application.

## Examples

- [Mattermost](guides/mattermost#lancement-du-service)
- [Memcached](guides/memcached#étape-2--lancement-du-service)
- [MongoDB](guides/mongodb#lancement-du-service)
- [Redis](guides/redis#lancement-du-service)

[^1]: `[compte]` to replace with the account name.

[^2]: see [service `systemd` "simple"](https://www.freedesktop.org/software/systemd/man/systemd.service.html#Type=) for examples.

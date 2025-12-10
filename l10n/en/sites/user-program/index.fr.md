+++
url = "/en/sites/user-program/"
title = "How to use the User Program type"
linkTitle = "User Program"
layout = "howto"
weight = 20
tags = [ "http", "user program", "site" ]
+++

To launch a web program that does not use one of the other types of site you can use the _User Program_.

It can be used for languages [Erlang](https://www.erlang.org/), [Go](languages/go), [Java](languages/java), [Lua](languages/lua), [Rust](https://www.rust-lang.org/), [Scala](https://www.scala-lang.org/), or many others. .[^1]

{{< fig "images/admin-panel_sites-list.png" "Admin interface: list of sites" >}}

- Name: Used for display in the alwaysdata admin interface purely informative;
- Addresses: the addresses to join your site (`*.example.org` for _catch-all_);

{{< fig "images/admin-panel_add-site-general.png" "Add site: manager" >}}

- Type: User Program;
- Command: command to be executed to launch the program. The HTTP server of your program must point to the IP and port given in the explanatory text;
- Work directory;
- Environment: environment variables that allow the program to work.

{{< fig "images/admin-panel_user-program.png" "Add Site: User Program" >}}

{{% notice tip %}}
Before setting up the site, you can test the launch of the program in [SSH](remote-access/ssh).
{{%/notice %}}

If the program does not run, the _sites_ logs available in the `$HOME/admin/logs/sites/` directory will help you.

[^1]: For example, [Nginx](https://www.nginx.com/), [LiteSpeed](https://www.litespeedtech.com/) or [Varnish](https://varnish-cache.org/) are usable on _alwaysdata_ servers. Installation and configuration are at your load.

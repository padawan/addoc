+++
url = "/advance/resources-alert-and-limitations systems"
title = "System resources: alerts and limitations"
layout = "howto"
hidden = true
tags = [ ]
+++

{{% notice note %}}
Functionality available only on [Cloud Private](accounts/billing/private-cloud-prices).
{{%/notice %}}

The **Resources** menu allows you to configure your system resources, such as disk space, CPU or memory:

{{< fig "images/admin-panel_resources.png" "" >}}

- _Disk space limit_: maximum limit that an account can reach for a moment T. If it is reached, an unavailability is expected.

- _CPU limit_: maximum limit that can reach an account at a moment T. If it is reached, delays or unavailability are expected.

- _RAM_ limit: maximum limit that an account can reach for a moment T. If it is reached a process (not forcefully the most consumer) is automatically killed by the system.

You can manage these three limits at _server_ or _account_ level. Account level values **take advantage** over server values.

- _RAM threshold_: threshold at which the current script is performed.

- _Execute command in case of RAM-threshold exceeding_: command/script executed by system when threshold is reached. This makes it possible not to kill a "random" process.

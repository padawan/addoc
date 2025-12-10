+++
url = "/statistics/"
title = "Statistics"
pre = "<i class='fas fa-fw fa-chart-line'></i> "
layout = "man"
weight = 35
tags = [ "http", "statistics", "site" ]
+++

From raw HTTP logs (`$HOME/admin/logs/http`) we will handle unique tour statistics[^1] in _real time_. These are available in the **Web > Analytics** section.

{{< fig "stats-panel.en.png" "" >}}

You can view the graph by site or for the whole account.

A server-level graph is available in the **HTTP > Analytics** menu for the [Private Cloud](accounts/billing/private-cloud-prices).

## Statistics customization

Our platform is based exclusively on HTTP logs and provides a simple interface. It is not possible to add custom settings.

Look at the installation of your own web statistics measurement software: [Matomo](https://matomo.org/) can be installed via our [marketplace](https://www.alwaysdata.com/fr/marketplace/). If you already have an alwaysdata account, go to the **Web > Sites > Install an App** menu to install it.

[^1]: IP estimate: From a few minutes without a request a single IP address will be re-visited.

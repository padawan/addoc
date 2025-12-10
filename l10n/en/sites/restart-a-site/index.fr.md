+++
url = "/sites/redemarrer-un-site/"
title = "How to restart a site"
layout = "howto"
hidden = true
tags = [ "http", "site" ]
+++

To take into account certain changes, it is necessary to restart the program. This is performed:

- when clicking the **restart** button;
- when making changes on the form of the site in **Web > Sites**:
  - when an address is added/modified/deleted;
  - when a site option is changed;
- when making changes in the **Environment** menu.

{{< fig "images/site-restart.png" "Restart button" >}}

These actions can also be accessed via our [API](api).

{{% notice info %}}
Only one Apache server exists per account. By restarting a site using this web server (PHP, Redirecting, Static Files and Custom Apache), all Apache sites in the account will be restarted.
{{%/notice %}}

## Hot restart

There is no universal method for requesting a _hot restart_ (during which no requests should be lost). By default the system sends a `SIGTERM`, which will stop the process and relaunch it. In this case, requests may potentially be lost.

For _Apache_ and _uWSGI_ web servers, signals to perform a hot reboot are managed by the system.

For other programs, the **hot restart** field allows you to specify which signal to send to the application.

{{< fig "images/hot-restart-signal.png" "" >}}

Examples:

- Ruby web server [Puma](https://github.com/puma/puma/blob/master/docs/restart.md)

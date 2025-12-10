+++
url = "/security/ssl-tls/configurer-tls/"
title = "Configure TLS"
layout = "howto"
hidden = true
tags = [ "http", "security", "site" ]
+++

[TLS](https://fr.wikipedia.org/wiki/Transport_Layer_Security) is a cryptographic protocol for storing exchanges over the internet.

Three profiles for HTTP connections are possible:

- _Modern_ : only TLS 1.3. Compatible with newest browsers;
- _Intermediary_ : TLS versions higher than 1.2 are enabled which allows to be compatible with most browsers;
- _Old_ : all versions of TLS are enabled which allows to be compatible with older browsers.

{{% notice note %}}
The _Intermediary_ profile is active by default on the alwaysdata servers.
{{%/notice %}}

{{< fig "images/account-tls-configuration.png" "Admin interface: configure TLS at account level" >}}

## Private Cloud

{{< fig "images/server-tls-configuration.png" "Admin interface: configure TLS at server level" >}}

+++
url = "/domaines/dnssec/"
title = "DNSSEC"
layout = "man"
hidden = true
tags = [ "dns", "domain", "security" ]
+++

[DNSSEC](https://fr.wikipedia.org/wiki/Domain_Name_System_Security_Extensions) adds cryptographic signatures to existing DNS records. This authenticates the origin of the data and ensures that it has not been modified in transit.

Setting up DNSSEC is done both on authoritarian DNS servers and on the registrar of a domain:

- a private key must be configured on authoritarian DNS servers;
- and its public key, at the registrar.

## Set up at alwaysdata

Go to **Domains > [example.org] Details - ⚙️ > DNSSEC**

### Domain is registered via alwaysdata and uses alwaysdata DNS servers

{{< fig "images/allad-step1.en.png" "" >}}

Click **Enable**.

{{< fig "images/allad-step2.en.png" "" >}}

This will create the keypair that will be configured on our DNS servers and at the registrar.

### Domain is registered via alwaysdata but uses external DNS servers

{{< fig "images/registerad-step1.en.png" "" >}}

Create the key pair at your DNS provider, and then click **Add a public key** containing the elements that your DNS provider will give you.

{{< fig "images/registerad-step2.en.png" "" >}}

We will then configure this public key at the registrar.

### Domain is not registered via alwaysdata but uses alwaysdata DNS servers

{{< fig "images/dnsad-step1.png" "" >}}

Click **Enable**. This will create the key pair.

{{< fig "images/dnsad-step2.en.png" "" >}}

Then copy the key and enter it at your registrar.

## Links

- [RFC 4033](https://datatracker.ietf.org/doc/html/rfc4033)
- [RFC 4034](https://datatracker.ietf.org/doc/html/rfc4034)
- [RFC 4035](https://datatracker.ietf.org/doc/html/rfc4035)

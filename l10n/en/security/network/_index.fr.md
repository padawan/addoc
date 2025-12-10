+++
url = "/security/network"
title = "Network"
weight = 30
layout = "man"
tags = [ "infrastructure", "security" ]
+++

## Firewall (firewall)

Owner of [Private Cloud](accounts/billing/private-cloud-prices) can [set their firewall](configure-firewall) directly in their admin interface via the server's **Firewall** menu.

### Incoming Firewall

Users cannot listen on any port, only the necessary ones are open.

### Outgoing Firewall

All ports are open without filtering, so you can define your own uses without our contest. Any connection is proud and will be temporarily blocked in the event of abuse.

## Prevention of intrusions

alwaysdata uses [Fail2ban](http://www.fail2ban.org/) as a intrusion prevention system on all its servers. This parses connection logs for different services and will block IPs for a period of 10 minutes after about fifty login attempts failed within 10 minutes.

You can also set up an [application firewall](sites/waf) directly in your account to protect your websites from malicious attacks.

## DDoS

An [DDoS]attack (https://fr.wikipedia.org/wiki/Attaque_par_d%C3%A9ni_de_service) aims to make a server, service or infrastructure unavailable. It can take different forms: saturation of bandwidth, depletion of system resources of the machine...

All alwaysdata servers are configured with 3/4 level DDoS protection according to [OSI](https://fr.wikipedia.org/wiki/Mod%C3%A8le_OSI). You can manage the application.

Private Cloud users can contact the [support](https://admin.alwaysdata.com/support/add/) for help installing or intervening.







+++
url = "/architecture/"
title = "Alwaysdata architecture"
pre = "<i class='fas fa-fw fa-atom'></i> "
weight = 40
archetype = "chapter"
tags = [ "technical environment", "infrastructure" ]
+++

## Master Architecture

Our servers are hosted in France, in Paris region. We rely on the expertise of[Equinix](https://www.equinix.com/) for our main datacenters. They certify us a level of availability of more than 99.99999% ([Equinix Certifications](https://www.equinix.co.uk/data-centers/design/standards-compliance)).

alwaysdata is the owner of its infrastructure - servers, storage bays, network equipment and anything to support our platform.

We will host our own _independent network_: [AS60362](http://as60362.net/).

All our network equipment, switches, Pair routers (two different manufacturers) and four independent network utilities ensure redundancy and neutrality of our network.

All our machines are equipped with SSD configured in RAID1\* (duplicated in real time) and _hot-exchangeable_. Their feedings are _redundant_ via two independent electricity chains and spare equipment is available at our production sites to replace any defective components.

We natively support _IPv6_ for all of our services.

To go further:

- [Réseau](security/network)
- [IP ranges](security/ip-ranges)
- [Business Continuity Plan](security/drp)

## Software Architecture

We use as many open source solutions as possible and our servers run on [Linux Debian x64](https://www.debian.org/). All our services are remotely accessible and a [REST API](api) is available for configuration operations on our admin interface.

Each account is segregated from others via an [Cgroups](https://fr.wikipedia.org/wiki/Cgroups). It executes its own programs, its own HTTP servers to provide enhanced security and customization.

Our system automatically distributes available resources, evenly between all accounts of a server. When an account encounters peak consumption, the platform redistributes its resources by raising small or non-active accounts to temporarily reassign them.

- [HTTP Stack](sites/http-stack)
- [Security Updates](security/security-upgrades)

---

- [Bug Bounty](security/bug-bounty)

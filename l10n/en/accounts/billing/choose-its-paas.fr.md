+++
url = "/accounts/billing/choose-son-plan/"
title = "Which offer should I choose?"
linkTitle = "Choose your hosting plan"
layout = "man"
weight = 1
tags = [
  "public cloud",
  "invoicing",
  "server assigned",
  "gold server"
]
+++

The alwaysdata hosting offer is qualified as [Platform-as-a-Service](https://fr.wikipedia.org/wiki/Plate-forme_en_tant_que_service)[^1] : it provides the infrastructure (data center, network, plant machines, etc. and the system stack (OS[^2], interpre­pre­ers, libraries, databases, etc. ). Users are only responsible for the implementation, maintenance and updates of their applications.

alwaysdata offers several types of environment:

| Name                                                                        |           | Description                                                                    |
| --------------------------------------------------------------------------- | --------- | ------------------------------------------------------------------------------ |
| [Public Cloud](accounts/billing/public-cloud-prices) / Free and More Offers |           | Hosting account dispatched on multiple servers - hosting hundreds of users     |
|                                                                             |           | GTI 1h, GTR 4h, Availability Rate 99.7%                        |
| [Private Cloud](accounts/billing/private-cloud-prices) / Max Offers         | Dedicated | Physical server used only one user                                             |
|                                                                             |           | Account isolation without additional billing                                   |
|                                                                             |           | GTI 15min, GTR 1h, Availability Rate 99.9%                     |
|                                                                             | Gold      | Physical server rebooked to a single user, **redundant** in another datacenter |
|                                                                             |           | Account isolation without additional billing                                   |
|                                                                             |           | GTI 15min, GTR 1 hour, Availability Rate 99.95%                |

For all these offers the number of sites, domains, databases, emails (...) is unlimited.

---

\| Services || Cloud Public | Cloud Privé |
\|---|---|---|---|---|
|||| **Dédié** | **Gold** |
\| Support | Tickets |✔️|✔️|✔️|
|| [Tickets urgents](accounts/urgent-ticket) |❌|✔️|✔️|
|| Téléphone |❌|✔️|✔️|
\| Sites web | Serveur HTTP configurable |✔️|✔️|✔️|
|| [Applithèque](marketplace) |✔️|✔️|✔️|
|| [SSL Let's Encrypt](security/ssl-tls/lets-encrypt) |✔️|✔️|✔️|
|| [Cache HTTP](sites/http-cache) |✔️|✔️|✔️|
|| [WAF](sites/waf) |✔️|✔️|✔️|
|| [Statistiques de visites](analytics)|✔️|✔️|✔️|
|| [Sondes de monitoring](sites/use-probes) |❌|✔️|✔️|
|| Conseils d'optimisation |❌|✔️|✔️|
\| Langages | [PHP](languages/php) |✔️|✔️|✔️|
|| [Python](languages/python) |✔️|✔️|✔️|
|| [Ruby](languages/ruby) |✔️|✔️|✔️|
|| [Node.js](languages/nodejs) |✔️|✔️|✔️|
|| [Java](languages/java) |✔️|✔️|✔️|
|| [Deno](languages/deno) |✔️|✔️|✔️|
|| [Elixir](languages/elixir) |✔️|✔️|✔️|
|| [Lua](languages/lua) |✔️|✔️|✔️|
|| [Go](languages/go) |✔️|✔️|✔️|
|| [Tout autre langage](languages) |✔️|✔️|✔️|
\| Bases de données[^3] | [MariaDB (MySQL)](databases/mariadb) |✔️|✔️|✔️|
|| [PostgreSQL](databases/postgresql) |✔️|✔️|✔️|
|| [RabbitMQ](databases/rabbitmq) |✔️|✔️|✔️|
|| [Memcached](databases/memcached) |❌|✔️|✔️|
|| [Redis](databases/redis) |❌|✔️|✔️|
|| [ElasticSearch](databases/elasticsearch) |❌|✔️|✔️|
|| Autres |❌|Sur demande et après analyse de notre équipe technique|Sur demande et après analyse de notre équipe technique|
\| Emails | Configuration personnalisable |✔️|✔️|✔️|
|| [Filtrage via scripts Sieve](e-mails/use-sieve-scripts) |✔️|✔️|✔️|
|| [Listes de diffusion](e-mails/mailing-lists) |✔️|✔️|✔️|
|| [File d'attente SMTP](e-mails/smtp-queue) |❌|✔️|✔️|
|| [Relais SMTP](e-mails/smtp-relay) |❌|✔️|✔️|
\| Accès distant | [FTP](remote-access/ftp) |✔️|✔️|✔️|
|| [SFTP](remote-access/sftp) |✔️|✔️|✔️|
|| [SSH](remote-access/ssh) |✔️|✔️|✔️|
|| [WebDAV](remote-access/webdav) |✔️|✔️|✔️|
\| Sauvegardes[^4] ||✔️|✔️|✔️|
\| Autres | [API](api) |✔️|✔️|✔️|
|| [Tâches planifiées](tasks) |✔️|✔️|✔️|
|| Services[^5] |✔️|✔️|✔️|
|| [Gestion du firewall](security/network/configure-firewall) |❌|✔️|✔️|
|| [Docker](advanced/docker) |❌|✔️|✔️|
|| [VPN](security/vpn) |❌|✔️|✔️|
|| Réplication SGBD |❌|Sur demande|✔️|
|| Réplication des données en temps réel |❌|❌|✔️|

Migrating to a higher offer is possible and free of charge: in the _Subscriptions_ tab in case of a change of pack in Public Cloud or by contacting the [support](https://admin.alwaysdata.com/support/add/) to switch to another environment.

{{% notice note %}}
A _optimized_ app will have the same performance regardless of the type of environment it is on. However, _minus users_ on a server enhances more **stability** and **comfort** (eliminating variations in performance due to other users).
{{%/notice %}}

[^1]: As a result, users do not have root permissions and cannot use `sudo`. The installation of many services can be done directly at the account level, and [Private Cloud] (accounts/billing/private-cloud-prices) users can request support for services that would not be the case.

[^2]: Our infrastructure is based on the Debian operating system.

[^3]: Database **info** by alwaysdata. It is also possible to install them via the [services](services). The information for these services will then not be performed by alwaysdata. In Private Cloud, RDBMS is installed on demand and can be added after server installation.

[^4]: Daily [Sauvegardes](backups) and directly accessible in the account. Depending on the offer selected, they are kept for up to 30 slippery days.

[^5]: [Generic Programs](services) to work 24 hours a day.

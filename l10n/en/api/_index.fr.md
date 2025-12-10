+++
url = "/api/"
title = "API"
pre = "<i class='fas fa-fw fa-plug'></i> "
weight = 80
tags = [ "api", "admin interface" ]
+++

An [API](https://fr.wikipedia.org/wiki/Interface_de_programmation) (for Application
Programming Interface) is a programming interface that automates
the management of your resources.

Our API [REST](https://fr.wikipedia.org/wiki/Representational_State_Transfer)
allows you to control your alwaysdata resources (accounts, emails, databases,
etc.) from your code.

## Addresses

| Version             | Root URL                                              | Documentation                                                                   |
| :------------------ | :---------------------------------------------------- | :------------------------------------------------------------------------------ |
| 1.0 | api.alwaysdata.com/v1 | https://api.alwaysdata.com/doc/ |

## Quick Examples

```sh
$ curl --basic --user "APIKEY account=foo:" https://api.alwaysdata.com/v1/mailbox/
```

### Restart a site

```sh
$ curl -X POST --basic --user "APIKEY account=foo:" https://api.alwaysdata.com/v1/site/1234/restart/
```

`APIKEY` to replace with the [API token](accounts/tokens), `foo` with the account name concerned and `1234` with the site ID.

## Know all

- [Utilisation](api/usage)
- [Exemples](examples)
- [Ressources](api/resources)

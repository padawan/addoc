+++
url = "/avance/migrations/migration-cloud-prive/"
title = "How to Migrate to Private Cloud"
layout = "howto"
hidden = true
tags = [ "migration" ]
+++

Most migration involves a global change on the server. For example, migrating to a new version of our software infrastructure will require a complete reinstallation of the server.

On the Public Cloud, when migrating, accounts are migrated to a new server that runs the new version. When you have a Private Cloud, this is not possible: you only have one server.

## Mandatory Migrations

To avoid having to perform the brutal migration of your server, and thus of all the accounts found there, [they are done in several steps](advanced/migrations/private-cloud-migrations/required-migrations-process).

## Optional migrations

Some migration related only to a service from our infrastructure (example: database management servers) may be proposed.

In this case, no preparations, no test is possible, the update is performed directly on the server. However, you can open an account on the Public Cloud if this service is offered to test some of your applications.

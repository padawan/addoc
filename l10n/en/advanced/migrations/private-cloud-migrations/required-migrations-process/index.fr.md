+++
url = "/avance/migrations/migration-cloud-prive/deroulement-migrations-compulsory"
title = "Cloud Privacy: Mandatory migration overflow"
layout = "man"
hidden = true
tags = [ "migration" ]
+++

These migrations are performed in four hands with the [support](https://admin.alwaysdata.com/support/).

## Recommended

### Step 1 - Making the necessary changes

The user preparses all the accounts of the server following the recommendations of the documentation page (as in the Public Cloud). It is possible to go back and correct problematic behaviors.

This step is used to test the move of the databases, check the connection parameters of its software...

> Test servers are available for databases.

Once an account is migrated to the transit server it will also be possible to backtrack and override the old infrastructure _temporarily_ in case of trouble.

{{< fig "images/migration-1.png" "" >}}

## Required

### Step 2 - Requesting the transit server

**All accounts are available.** The user must contact support to arrange a transit server.

{{< fig "images/migration-2.en.png" "" >}}

### Step 3 - Installing the transit server

Support provides the transit server of a configuration to the client server. The installation can take several hours and precopy files and mails to the transit server.

> This step depends on the availability of transit servers corresponding to the configuration of the client server on the day of the request. **There may be some waiting.**

{{< fig "images/migration-3.en.png" "" >}}

### Step 4 - Migrating accounts to new infrastructure

The transit server is ready. User can migrate accounts - one by one - to the transit server, via the **Migrations** menu of the server interface or the **Advanced> Migrations** menu of the account interface.

> The user is **autonomous** in this step. It can migrate whenever it wishes.

Migrating accounts is a split per account of a few seconds in a few hours; depending on the size of each account (particle of the databases). There is one minute of unavailability per giga of data bases.

{{< fig "images/migration-4.en.png" "" >}}

{{% notice tip %}}
For domains not using alwaysdata DNS, no need to do IP change - _A and AAAA_ records. The client server will redirect transparently.
{{%/notice %}}

### Step 5 - Check after migration

The user can make application changes once an account migrates if needed.

> It is also possible to go back and _temporarily_ over the old infrastructure in case of trouble.

Once all accounts are migrated, it will contact support so that the one proceeds to reinstall its server.

{{< fig "images/migration-5.en.png" "" >}}

### Step 6 - Reinstalling the client server

**All accounts are migrated to the new software infrastructure and are on the transit server.**

Support reinstalls the client server to run on the new infrastructure. This can take several hours and precopy files and mails.

> Temporary backtracking is no longer possible.

{{< fig "images/migration-6.en.png" "" >}}

{{% notice note %}}
During this operation, client server IP addresses are rerouted to the transit server so that services remain accessible normally. However, a short period of unavailability of these IPs (around one minute) is to be expected. \*In case user uses alwaysdata DNS servers traffic will have been redirected to the transit server IP addresses of the account migration - there is no unavailability period to expect.
{{% /notice %}}

### Step 7 - Finalization: Removing accounts to the client server

**The client server is reinstalled.** Support contacts the user to move the accounts. _This finalization step can be performed by the support in time and working days or by the user._

This final relocation of accounts will result in a breakdown per account equal to the unavailability on the first migration.

{{< fig "images/migration-7.en.png" "" >}}

### Step 8 - Officially finished migration

All accounts have been relocated to the reinstalled client server.

{{< fig "images/migration-8.png" "" >}}

## Notes

- The transit server is available for uninterrupted migration for a period of **up to two weeks**. If the user did not complete the migration of all his accounts at the end of this period, the transit server will be invoiced at the same time as the client server (in prorata, day per day) — in addition to the original server that is invoiced normally.

- If the user wants to test the migration on some accounts before launching the actual migration or if they want to have access to a longer transit server (_without paying_), it can take advantage of our shared transit server to all dedicated clients and VPS. Neanmin:
  - this server may not match the client server configuration;
  - no precopy of files and emails is performed: the migration time can therefore be extended;
  - users do not have access to the server customizations and firewall they have set;
  - the availability of this shared transit server is validated on a case-by-case basis by the support based on the characteristics of the client server and its accounts.

- If the user is in charge of the finalization step, he has **one week** to move all accounts without overcrowding.

> The Noun Project

+++
url = "/accounts/permissions/"
title = "Permissions"
weight = 12
layout = "man"
tags = [ "invoicing", "technical environment", "admin interface" ]
+++

Because hosting your data often involves different players, our administration interface allows you to grant permissions on different granularity levels.

You can set permissions through the **Permissions** menu in your client space.

{{< fig "images/menu.png" "" >}}

## Global Permissions

- **Account Management**: Lets you open accounts with your associates (_Subscriptions_);
- **[Facturation](accounts/billing)** : allows accounting or administrative services to receive an alert when your account balance is negative or when opening a billing ticket by our services and pay invoices, buy/renew/transmit domains (_Billing_ menu);
- **Account-level Technique**: allows technical teams to manage the purely technical aspect of your accommodation (websites, emails, databases..) without worrying about its management and billing;
- **Server level technique**: available on [Private Cloud](accounts/billing/private-cloud-prices), your network administrator will be able to manage firewall settings, email queue, and many more...

## Technical permissions

Whether it's for the purely technical aspect of your accounts or servers, your organization imposes a decoupling of the technical responsibilities internally between several persons or groups of persons or between external subcontractors who need even restricted access. So you can set permissions by **service** and by **account** or **server**.

### By account

From time to time a profile has account permissions, it has access to the _Server Status_ menu.

- **Technical contacts** : be alerted when opening a technical ticket by our account departments;
- **Consommation** : Track disk space usage (_Disk space_, _Advanced > Logs_) menus;
- **Ressources** : permission for accounts on [Private Cloud](accounts/billing/private-cloud-prices) allows to manage [sondes](sites/use-probes) (_Web > Sondes_ menu\*) and [ressources](advanced/system-resources-alerts-and-limitations) (_Advanced > Resources_);
- **[Statistiques](analytics)** : analyze visits to your sites (menu _Web > Analytics_);
- **[Sites](sites)** : configure websites and Apache environment (menus _Web > Sites_, _Web > Configuration_);
- **[Domaines](domains)** technically manage domains and their DNS (_Domains_ menu). For all invoicable actions, you will also need the **Facturation** permissions on the proprietary profile;
- **[Emails](e-mails)** (menus _Emails > Addresses_, _Emails > Mailings_, _Emails > Configuration_);
- **[Email history sent](e-mails/check-email-sending)** (menu _Emails > History_);
- **[Databases](databases)** (menu _Databases_);
- **[FTP](remote-access/ftp)** (menu _Remote access > FTP_);
- **[SSH](remote-access/ssh)** (menu _Remote access > SSH_);
- **[WebDAV](remote-access/webdav)** (menu _Remote access > WebDAV_);
- **[Environnement](/languages)**: configure programming languages (menu _Environment_);
- **Processus** : running process that can be analyzed or killed (menu _Advanced > Processes_);
- **[IP Addresses](advanced/dedicated-ip-addresses)** : Rent dedicated IP addresses for HTTP or SMTP (menu _Advanced > IP Addresses_);
- **[SSL Certificates](security/ssl-tls)** (menu _Advanced > SSL Certificates_);
- **[Migration](advanced/migrations)** (_Advanced> Migrations_);
- **[Scheduled Tasks](tasks)** (menu _Advanced > Scheduled Tasks_);
- **[Sauvegardes](backups)** (menu _Advanced > Backup restore_);
- **[Services](services)** (menu _Advanced > Services_).

### By server

From the moment on or before a profile has permissions on the server, it has access to the _Configuration_ menu.

- **Technical contacts** : be alerted when opening a technical ticket by our services regarding a server;
- **[SSH Users](remote-access/ssh/install-globally-ssh-keys)**: Install SSH keys for simplified access to different accounts (menu _SSH Keys_);
- **[Firewall Reggles](security/network/configure-firewall)** : create firewall files and view automatic IP ban at server level (_Firewall_ menu);
- **SMTP** configuration: Manage email sending queue, SMTP relay and spam score (_SMTP menu_);
- **Database Users** : Give global access to all accounts databases (_MySQL Users_);
- **SSL Configuration** : choose the SSL certificate to return to the server (`*.alwaysdata. and` by default) and the server's [TLS configuration](security/ssl-tls/configure-tls) (_SSL_ menu);
- **HTTP** configuration: choose a website that will be the [default homepage](sites/misc#site-http-par-defaut) and [log retention period](remote-access/admin-directory#logs) (_HTTP_ menu);
- **Consommation** : Access a set of information about your server (Accounts menu, Server Status). To open accounts on the server it will be necessary to have **Account Management** permission on the proprietary profile;
- **[Ressources](advanced/system-resources-alerts-and-limitations)** : modify resources limitations per account - RAM, CPU, disk space (_Resources_ menu).
- **[Migration](advanced/migrations)** (_Migrations_ menu);

## 2FA Required

When the **2FA needed** checkbox is checked, the user must login [with 2 factors](security/two-factor-authentication) to access the menus they have been given access.

## My Permissions

It is possible to remove the permissions we have on other profiles from the **Permissions > My Permissions** menu. The deletion is not done fine, they will all be deleted.

## Misc

By creating permissions to an email address that does not have an alwaysdata profile, this person will receive an email to initialize their profile.

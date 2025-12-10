+++
url = "/fr/comptes/permissions/"
title = "Permissions"
weight = 12
layout = "man"
tags = [
  "facturation",
  "environnement technique",
  "interface d'administration"
]
+++

Parce que l'hébergement de vos données implique très souvent différents acteurs, notre interface d'administration vous permet d'octroyer des permissions sur différents niveaux de granularité.

Vous pouvez paramétrer les permissions via le menu **Permissions** de votre espace client.

{{< fig "images/menu.fr.png" "" >}}

## Permissions globales

- **Gestion des comptes** : délègue l'ouverture de comptes à vos associés (menu _Abonnements_)  ;
- **[Facturation](accounts/billing)** : permet aux services comptables ou administratifs de recevoir une alerte lorsque le solde de votre compte est négatif ou lors de l'ouverture d'un ticket concernant la facturation par nos services et de payer les factures, acheter/renouveler/transférer les domaines (menu _Facturation_) ;
- **Technique au niveau des comptes** : permet aux équipes techniques de gérer l'aspect purement technique de votre hébergement (sites, emails, bases de données..) sans se soucier de sa gestion et facturation ;
- **Technique au niveau des serveurs** : disponible sur [Cloud Privé](accounts/billing/private-cloud-prices), votre administrateur réseau pourra gérer règles de firewall, queue d'envoi des emails et bien d'autres...

## Permissions techniques

Que ce soit pour l'aspect purement technique de vos comptes ou de vos serveurs, votre organisation impose un découpage des responsabilités techniques en interne entre plusieurs personnes ou groupes de personnes ou entre sous-traitants externes qui ont besoin d'accès même restreints. Vous pouvez donc définir des permissions par **service** et par **compte** ou **serveur**.

### Par compte

À partir du moment où un profil a des permissions sur le compte, il a accès au menu _Statut des serveurs_.

- **Contact technique** : soyez alerté lors de l'ouverture d'un ticket technique par nos services concernant le compte ;
- **Consommation** : suivez la consommation d'espace disque (menus _Espace disque_, _Avancé > Logs_) ;
- **Ressources** : permission pour les comptes sur [Cloud privé](accounts/billing/private-cloud-prices) permet de gérer les [sondes](sites/use-probes) (menu _Web > Sondes_) et [ressources](advanced/system-resources-alerts-and-limitations) (menu _Avancé > Ressources_) ;
- **[Statistiques](analytics)** : analysez les visites de vos sites (menu _Web > Analytics_)  ;
- **[Sites](sites)** : configurez les sites web et l'environnement Apache (menus _Web > Sites_, _Web > Configuration_) ;
- **[Domaines](domains)** gérez techniquement les domaines et leurs DNS (menu _Domaines_). Pour toutes les opérations facturables, il faudra aussi les permissions **Facturation** sur le profil propriétaire ;
- **[Emails](e-mails)** (menus _Emails > Adresses_, _Emails > Listes de diffusion_, _Emails > Configuration_) ;
- **[Historique des emails envoyés](e-mails/check-email-sending)** (menu _Emails > Historique_) ;
- **[Bases de données](databases)** (menu _Bases de données_) ;
- **[FTP](remote-access/ftp)** (menu _Accès distant > FTP_) ;
- **[SSH](remote-access/ssh)** (menu _Accès distant > SSH_) ;
- **[WebDAV](remote-access/webdav)** (menu _Accès distant > WebDAV_) ;
- **[Environnement](/languages)** : configurez les langages de programmation (menu _Environnement_) ;
- **Processus** : processus en cours d'exécution pouvant être analysés ou tués (menu _Avancé > Processus_) ;
- **[Adresses IP](advanced/dedicated-ip-addresses)** : louer des IP dédiées pour HTTP ou SMTP (menu _Avancé > Adresses IP_) ;
- **[Certificats SSL](security/ssl-tls)** (menu _Avancé > Certificats SSL_) ;
- **[Migration](advanced/migrations)** (menu _Avancé > Migrations_) ;
- **[Tâches planifiées](tasks)** (menu _Avancé > Tâches planifiées_) ;
- **[Sauvegardes](backups)** (menu _Avancé > Restauration de sauvegardes_) ;
- **[Services](services)** (menu _Avancé > Services_).

### Par serveur

À partir du moment où un profil a des permissions sur le serveur, il a accès au menu _Configuration_.

- **Contact technique** : soyez alerté lors de l'ouverture d'un ticket technique par nos services concernant un serveur ;
- **[Utilisateurs SSH](remote-access/ssh/install-globally-ssh-keys)** : installez des clés SSH pour un accès simplifié aux différents comptes (menu _Clés SSH_);
- **[Règles firewall](security/network/configure-firewall)** : créez des règles firewall et consultez le bannissement automatique d'IP au niveau du serveur  (menu _Firewall_);
- **Configuration SMTP** : gérez la queue d'envoi d'emails, le relais SMTP et le score de spam (menu _SMTP_);
- **Utilisateurs base de données** : donnez un accès global aux bases de données de l'ensemble des comptes (menu _Utilisateurs MySQL_) ;
- **Configuration SSL** : choisissez le certificat SSL à retourner sur le serveur (`*.alwaysdata.net` par défaut) et la [configuration TLS](security/ssl-tls/configure-tls) du serveur (menu _SSL_) ;
- **Configuration HTTP** : choisissez un site web qui sera la [page d'accueil par défaut](sites/misc#site-http-par-defaut) et la [période de rétention des logs](remote-access/admin-directory#logs) (menu _HTTP_) ;
- **Consommation** : accédez à un ensemble d'information sur votre serveur (menus Comptes, Statut du serveur). Pour ouvrir des comptes sur le serveur il sera nécessaire d'avoir la permission **Gestion des comptes** sur le profil propriétaire ;
- **[Ressources](advanced/system-resources-alerts-and-limitations)** : modifiez les limitations de ressources par compte - RAM, CPU, espace disque (menu _Ressources_).
- **[Migration](advanced/migrations)** (menu _Migrations_) ;

## 2FA nécessaire

Lorsque la case **2FA nécessaire** est cochée, l'utilisateur en question doit se connecter [avec 2 facteurs](security/two-factor-authentication) pour accéder aux menus auxquels on lui a donné accès.

## Mes permissions

Il est possible de supprimer les permissions que nous avons sur d'autres profils via le menu **Permissions > Mes permissions**. La suppression ne s'effectue pas finement, elles le seront toutes.

## Divers

En créant des permissions à une adresse email n'ayant pas de profil alwaysdata, cette personne recevra un email pour initialiser son profil.

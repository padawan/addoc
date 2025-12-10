+++
url = "/fr/emails/clients/apple-ios/"
title = "Comment configurer Mail (Apple/iOS)"
layout = "howto"
tags = [ "email", "ios", "macos", "apple" ]
hidden = true
+++

Dans nos exemples nous considérons les informations suivantes :

- Nom du compte : `test`
- Adresse email : `test@alwaysdata.net`

Elles sont à remplacer par vos informations de connexion personnelles :

| Serveur | Service | Information                |                                                                                                                    |
| ------- | ------- | -------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| Entrant | IMAP    | Nom d'hôte                 | imap-_[compte]_.alwaysdata.net |
|         |         | Port                       | 993                                                                                                                |
|         |         | Nom d'utilisateur          | Votre adresse email - par exemple _contact\@example.org_                             |
|         |         | Mot de passe               | Le mot de passe de votre adresse email                                                                             |
|         |         | Méthode d'authentification | Mot de passe normal                                                                                                |
|         | POP3    | Nom d'hôte                 | pop-_[compte]_.alwaysdata.net  |
|         |         | Port                       | 995                                                                                                                |
|         |         | Nom d'utilisateur          | Votre adresse email - par exemple _contact\@example.org_                             |
|         |         | Mot de passe               | Le mot de passe de votre adresse email                                                                             |
|         |         | Méthode d'authentification | Mot de passe normal                                                                                                |
| Sortant | SMTP    | Nom d'hôte                 | smtp-_[compte]_.alwaysdata.net |
|         |         | Port                       | 465                                                                                                                |
|         |         | Nom d'utilisateur          | Votre adresse email - par exemple _contact\@example.org_                             |
|         |         | Mot de passe               | Le mot de passe de votre adresse email                                                                             |
|         |         | Méthode d'authentification | Mot de passe normal                                                                                                |

{{% notice tip %}}
_[compte]_ doit être remplacé par le nom de votre compte et _contact\@example.org_ par votre adresse email. Ils sont définis dans le menu **Emails > Adresses** de notre interface d'administration.
{{% /notice %}}

## MacOS : application Mail

Rendez-vous dans **Fichier > Ajouter un compte > Autre compte Mail...**

- Indiquez les informations de connexion et choisissez entre IMAP ou POP pour le courrier _entrant_ ;
- Si vous recevez un message d'erreur SSL, cliquez quand même sur **Connecter**, vous pourrez ensuite renseigner de nouveau les informations de connexion.

Laissez l'authentification par mot de passe.

## iOS (iPhone, iPad) : application Mail

{{< fig "images/mail_ipad.fr.png" "Mail sur mobile" >}}

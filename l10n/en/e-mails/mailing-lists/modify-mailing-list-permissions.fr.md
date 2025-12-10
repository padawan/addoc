+++
url = "/fr/listes-de-diffusion/modifier-les-permissions-d-une-liste-de-diffusion/"
title = "Modifier les permissions d'une liste de diffusion"
layout = "man"
hidden = true
tags = [ "email", "mailing list" ]
+++

Pour modifier les permissions de diffusion d'une liste, vous devez vous connecter à l'[interface de gestion Postorius](https://mailman.alwaysdata.com/). Connectez-vous à l'aide d'une adresse mail d'administration que vous aurez défini à la [création de votre liste de diffusion](create-a-mailing-list).

Une fois identifié, rendez vous dans la section de gestion de la liste de diffusion concernée en cliquant sur son nom.

## Modération des contenus

Pour modifier les règles de diffusion, rendez vous dans la rubrique **Paramètres → Message Acceptance**. Vous pouvez y définir plusieurs règles de diffusion :

- _Retenir en modération_ : les messages doivent être acceptés par un administrateur ou un modérateur pour être diffusés aux membres. C'est une modération _a priori_.
- _Rejeter_ : les messages sont supprimés et les administrateurs sont notifiés du rejet.
- _Éliminer_ : les messages sont supprimés, sans notification.
- _Accepter immédiatement_: aucune action n'est requise et les membres recevront le message.

Ces règles peuvent s'appliquer à deux typologies d'expéditeurs :

- _abonnés_ : action à prendre quand le message est envoyé par un membre de la liste.
- _non-abonnés_ : action à prendre quand le message est envoyé depuis une adresse externe à la liste.

## Exemples

Pour définir une **liste de diffusion ouverte**, réglez toutes les permissions à _Accepter immédiatement_ : n'importe qui pourra envoyer un message aux membres (dans le cas d'une liste de support par exemple).

Pour définir une **newsletter**, réglez toutes les permissions à _Éliminer_ : seuls les administrateurs peuvent envoyer un message aux membres.

Pour définir une adresse d'une **groupe de travail**, réglez les permissions des membres à _Accepter_ et les permissions des non-membres à _Retenir en modération_ : les membres peuvent échanger des messages sans modération, et les utilisateurs externes au groupe peuvent demander à envoyer des messages en les faisant valider _a priori_.

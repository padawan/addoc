+++
url = "/fr/avance/ressources-systemes-alertes-et-limitations"
title = "Ressources système : alertes et limitations"
layout = "howto"
hidden = true
tags = [ ]
+++

{{% notice note %}}
Fonctionnalité disponible uniquement sur les environnements [Cloud Privé](accounts/billing/private-cloud-prices).
{{% /notice %}}

Le menu **Ressources** permet de configurer ses ressources système, comme  l'espace disque, le CPU ou la mémoire :

{{< fig "images/admin-panel_resources.fr.png" "" >}}

- _Limite d'espace disque_ : limite maximale que peut atteindre un compte à un instant T. Si elle est atteinte, une indisponibilité est à prévoir.

- _Limite de CPU_ : limite maximale que peut atteindre un compte à un instant T. Si elle est atteinte, des lenteurs ou indisponibilités sont à prévoir.

- _Limite de RAM_ : limite maximale que peut atteindre un compte à un instant T. Si elle est atteinte un processus (pas forcément le plus consommateur) est automatiquement tué par le système.

Il est possible de gérer ces trois limites au niveau _serveur_ ou au niveau _compte_. Les valeurs au niveau du compte **prennent l'avantage** sur les valeurs serveurs.

- _Seuil de RAM_ : seuil auquel est effectué le script présenté dessous.

- _Commande à exécuter en cas de dépassement du seuil de RAM_ : commande/script exécuté par le système lorsque le seuil est atteint. Cela permet de ne pas tuer un processus "au hasard".

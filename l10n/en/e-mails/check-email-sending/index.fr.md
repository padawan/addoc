+++
url = "/fr/emails/verifier-l-envoi-d-un-email/"
title = "Comment vérifier si un email a bien été envoyé"
hidden = true
layout = "howto"
tags = [ "email" ]
+++

Vous avez accès aux logs d'envois dans le menu **Emails > Historique**.

{{< fig "images/history.fr.png" "Liste des derniers envois" >}}

- _[Score](e-mails/delivery#système-de-notation)_ : score donné par l'antispam d'alwaysdata qui détermine si un email est envoyé ou non[^1] ;
- _Bloqué_ : si l'email a été bloqué par l'antispam d'alwaysdata. À ne pas confondre avec un _bounce_[^2] qui englobe d'autres raisons.

{{< fig "images/example.fr.png" "Exemple d'un envoi" >}}

- _Score interne_ : score donné par l'antispam d'alwaysdata ;
- _Rapport interne_ : détails du score donné par l'antispam d'alwaysdata. Il tient compte du score Rspamd ;
- _Score SPAM_ : score [Rspamd](https://www.rspamd.com/) ;
- _Rapport SPAM_ : détails du score Rspamd.

Seuls les emails envoyés durant les _12 derniers mois_ sont gardés et, par défaut, seuls les emails envoyés durant les _7 derniers jours_ sont affichés.

[^1]: un email avec un score supérieur à 3 ne sera pas envoyé en serveurs mutualisés. En Cloud Privé, la valeur par défaut est de 5 (modifiable).

[^2]: cela peut être un blocage de notre antispam, un refus par les serveurs destinataires ou encore une non-réponse de leur part pendant plusieurs jours par exemple. L'expéditeur doit alors recevoir un _Mail delivery failed_ reprenant les raisons du bounce.

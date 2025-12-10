+++
url = "/domaines/frequent-issues/"
title = "Domains - Frequent Issues"
layout = "faq"
weight = 90
tags = [ "troubleshooting", "domain" ]
+++

## Transfer

### "2304: Object status prohibited operation", "Transfer Prohibited from Registry Request" or "2308: Data management policy violation (domain [example.org] has invalid status (clientTransferProhibited)"

Protected domain against transfers a `whois` [^1] will return:

{{% notice %}}
Status: clientTransferProhibited
{{% /notice %}}

The protection must be removed from the current registrar.

### "Invalid Authorization Code"

Please make sure that no typing errors were performed by using the authorization code or re-set an authorization code.

{{% notice info %}}
To reassign it during an outgoing transfer contact our [support](https://admin.alwaysdata.com/support/add).
{{%/notice %}}

### "Registry error - 2308: Data management policy violation (domain expired)"

Domain expired, please try again before relaunching the transfer.

### "Transfer Refused by Registrar (Queue Message #[id])"

The current domain provider blocked the transfer. Contact them to know the cause of the transfer before relaunching.

## Ownership Change

### Max waiting duration for owner responses (15 days) reached.

A change of ownership must be accepted by the old and the new owner within a period of 15 days. Check the email addresses of both contacts.

## ICANN suspended domain

The[ICANN](https://www.icann.org/fr) checks email addresses of domain owners to make sure they are working properly. The owners have 15 days to validate the email sent by ICANN.

A `whois` will indicate the following message: `Domain Status: clientHold`

Dans l'interface d'administration alwaysdata, le message suivant - onglet **Domaines > Détails de [example.org] - 🔎 > Statut** - vous permettra de renvoyer l'email :

```
This domain was suspended by ICANN because its owner did not confirm its email address within 15 days of its creation, transfer or transfer.
```

If you do not know about the email address, you can change it in the contact details, menu **Domains > Contact Management**:

{{< fig "images/admin-panel_domains-list.png" "Admin interface: access to the Contact Management menu" >}}

{{< fig "images/admin-panel_contacts-management.en.png" "Admin interface: Contact management menu" >}}

## Links

- [EPP's status codes Glossary](https://www.icann.org/resources/pages/epp-status-codes-2014-06-16-en)

[^1]: More information about [whois](https://fr.wikipedia.org/wiki/Whois)

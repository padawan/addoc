+++
url = "/accounts/transfer-account/"
title = "Account cancellation"
layout = "man"
hidden = true
tags = [ "account", "profile" ]
+++

In some cases, it is not necessary to go through the transfer process and a change of profile information is sufficient. However, if the customer history should not follow, prefer the transfer.

## Profile Change

> For example, to follow up the sale of its company or the change of interlocutor. This is also what will have to be followed for a change of address.

Go to the **Profile** menu to edit profile information.

{{< fig "images/profile.en.png" "" >}}

Any profile information can be changed at the authentication level at the alwaysdata admin interface (email address) password) or property (name, address, surname). Future invoices will be issued with new profile information.

## MEN_CESSSES

> For example, only certain accounts are created, they are assigned to several people or the recipient is not receiving their customer history.

{{% notice warning %}}
[permissions](accounts/permissions) given to other profiles, support tickets, billing, actions performed on the alwaysdata admin interface and its API will all be _lost_.
{{%/notice %}}

Go to **Subscriptions > Treat to another user**. You will need to specify the email address of the recipient profile that will be able to accept it in the **Cessions** tab of their client interface.

{{< fig "images/accounts.en.png" "" >}}

{{% notice info %}}
Only the _account owner_ can initiate the assignment.
{{%/notice %}}

**This closes the current subscription and opens one on the recipient profile**. It is possible to assign an account in two ways:

- the recipient profile is invoiced _after acceptance of the assignment_. A pro rata refund is automatically executed on the issuer profile;
- The expiration date of the old subscription is kept and the recipient profile is only invoiced _in response_. No pro rata refunds will be made on the issuer profile.

As long as the new owner does not validate the assignment the issuer profile remains the owner of the account and can cancel it in the **Assignments** tab.

+++
url = "/en/mailing lists/modifier-les-permissions-d-une-mailing list/"
title = "Edit mailing list permissions"
layout = "man"
hidden = true
tags = [ "email", "mailing list" ]
+++

To change the mailing permissions of a list, you need to connect to the [Postorius management interface](https://mailman.alwaysdata.com/). Log in using an admin email address that you have set to [create your mailing list](create-a-mailing-list).

Once identified, go to the management section of the relevant mailing list by clicking on its name.

## Content Moderation

To change the broadcast settings, go to **Parameters → Message Acceptance**. You can define multiple broadcast sites:

- _Retain in Method_: Messages must be accepted by an administrator or model for dissemination to members. This is a _a priori_ pattern.
- _Reject_: Messages are deleted and admins are notified of rejection.
- _Remove_: messages are deleted, without notification.
- _Accept Immediate_: No action is required and members will receive the message.

These options can be applied to two types of senders:

- _subscriptions_: action to take when the message is sent by a member of the list.
- _Unsubscribe_: action to take when the message is sent from an external address to the list.

## Examples

To define an **open mailing list**, set all permissions to _Accept Unediting_: anyone will be able to send a message to members (for example a support list).

To set a **newsletter**, set all permissions to _Remove_: only administrators can send a message to members.

To define an address of a **workgroup**, set member permissions to _Accept_ and non-member permissions to _Keep mode_: members can exchange messages without models, and users outside the group can request to send messages by having them validated _a priori_.

+++
url = "/en/lists-de-diffusion/creer-ane-list-de-diffusion/"
title = "Create Mailing List"
layout = "man"
hidden = true
tags = [ "email", "mailing list" ]
+++

To create a mailing list, you need to log in to the alwaysdata admin interface - tab **Emails > Mailing Lists**.

## User management

{{% notice info %}}
You must define at least one admin user to manage your mailing list.
{{%/notice %}}

To define a new user for managing your mailing lists, go to the **User Management** section, then **Add User**.

If mailing lists have already been defined, you can already assign permissions to these lists to this new user.

{{% notice tip %}}
Users' email addresses do not need to belong to the same domain as the mailing list. For example, you can define a user `foo@bar.com` as administrator of the `baz@example.org` list.
{{%/notice %}}

## Mailing List Management

To define a new mailing list, go to **Add a mailing list**.

Define :

- a name for your mailing list that will be the local part of the email address of the list (e.g. for a mailing list behind the email address `foo@example. reg`, the list name will be `foo`);
- the domain the list is attached to. This domain must be available in the [list of domains](domains) where you have admin permissions;
- the permissions attached to the users you have defined in the _User Management_ section.

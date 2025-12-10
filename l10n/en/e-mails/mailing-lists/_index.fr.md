+++
url = "/en/mailing lists/"
title = "Mailing lists"
weight = 50
layout = "man"
tags = [ "email", "mailing list" ]
+++

Mailing lists (_mailing lists_) allow you to define a _pool_ of email addresses to return a message to. They are distinguished in their use by their broadcast capabilities:

- only "administrator" addresses are able to send content to registered receiving addresses (e.g. a newsletter);
- all participants can send messages to the list to allow a conversation (e.g. members of a workgroup).

**alwaysdata** allows you to define mailing lists at your convenience, connected to the domain(s) of your choice. They use open-source software [Mailman](https://docs.mailman3.org/projects/mailman/en/latest/) and their configuration relies on interface [Postorius](https://docs.mailman3.org/projects/postorius/en/latest/). You can refer to these documentation for their daily use.

## Login

The creation / modification / deletion of mailing lists is done from the admin interface: https://admin.alwaysdata.com/mailinglist/.

The internal management of mailing lists (members, permissions, etc) is done from the Postorius administration interface: https://mailman.alwaysdata.com/.

***

- [Create mailing list](create-a-mailing-list)
- [Add members manually to a list](add-members-to-a-mailing-list)
- [Edit Broadcast Rights](modify-mailing-list-permissions)
- [Add footer with default link](add-a-mailing-list-footer)

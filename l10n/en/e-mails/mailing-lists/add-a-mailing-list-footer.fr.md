+++
url = "/en/listes-de-diffusion/ajouter-un-foot-de-page-a-une-list-de-diffusion/"
title = "Add footer to mailing list"
layout = "man"
hidden = true
tags = [ "email", "mailing list" ]
+++

To add a footer to a mailing list, you need to connect to the [Postorius management interface](https://mailman.alwaysdata.com/). Log in using an admin email address that you have set to [create your mailing list](create-a-mailing-list).

Once identified, go to the management section of the relevant mailing list by clicking on its name.

## Using _Mode_

_Models_ allow you to define portions of content that can be injected or used in automatic messages in the list.

To finalize these, go to the _Models→ New Model_. The list of customizable templates is displayed, with their associated context. You then define the content of the template in the input area.

## Add a footer with an unsubscribe link

By default, messages sent to members do not contain an unsubscribe link. You can add this link by defining an automatic footer.

Add a `[list:member:regular:footer]` template with the following content:

```txt
--
Unsubscribe: <mailto:$short_listname-unsubscribe@$domain>
```

Each message posted to the list will be added a signature footer, containing the email address of the sincript managed from the _placeholders_ (e.g. `foo-unsubscribe@example. reg`).

+++
url = "/emails/reagir-envoi-spam/"
title = "How to react to spam sending"
layout = "howto"
hidden = true
tags = [ "email", "Infection", "spam" ]
+++

There are 3 main reasons for sending spam:

- [website infection](sites/clean-up-a-site);
- an attack on a website form;
- a password theft.

It is these last two that we are going to present here.

## Attack on form

When the alwaysdata team encounters an attack spamming on the form it will:

- stop sending by deactivating `POST` requests on the relevant site;
- delete all emails that are pending sending;
- Prevent user.

The user will have to set up more important protection on their form; for example, by using an [CAPTCHA](https://fr.wikipedia.org/wiki/CAPTCHA) for example.

The [WAF](sites/waf) may be useful for blocking certain attacks.

## Password Steal

In this case, it will:

- stop sending by changing the password of the concerned email address;
- delete all emails that are pending sending;
- Prevent user.

The user will then be able to enter a new password, **more secure**, to access their address again.

{{% notice info %}}
In the case of a refund, the alwaysdata team can _suspend_ the account waiting for the user to return.
{{%/notice %}}

> Test if your email address [has been compromised](https://haveibeenpwned.com/).

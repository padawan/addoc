+++
url = "/security/authentication-2-factors/"
title = "Admin: 2-factor authentication"
linkTitle = "2-factor authentication"
layout = "man"
weight = 10
tags = [ "2F", "profile", "security" ]
+++

[Two Factor Authentication](https://fr.wikipedia.org/wiki/Authentification_forte) allows _securing access to a portal_ by checking the identity of the person logging in through _two metrics_.

The technology chosen by alwaysdata is the [Time-based One Time Password](https://en.wikipedia.org/wiki/Time-based_One-time_Password_algorithm) (TOTP) algorithm: **sharing individual secret code and one-time use** between our database and strong client authentication applications.

{{< fig "images/profile-security.png" >}}
This will give you access to your personal codes (secret code and QR code).

You can then _configure your TOTP application_ which will return you a security code for single use to indicate when logging in to the administration interface. This security code was renewed every _30 seconds_ (computation based on time or counter).

{{% notice note %}}
In case of loss of two factor authentication, send an email to _contact[at]alwaysdata.com_ to disable it. [A check will be performed](accounts/admin-access-loss#blocage-lié-à-lauthentification-2-facteurshahahugoshortcode-s0-hbhb).
{{%/notice %}}

## OTP apps

- **[FreeOTP](https://freeotp.github.io/)**: [Android](https://play.google.com/store/apps/details?id=org.fedorahosted.freeotp), [iOS](https://itunes.apple.com/us/app/freeotp-authenticator/id872559395?mt=8) and [F-Droid](https://f-droid.org/packages/org.fedorahosted.freeotp) ([Github](https://github.com/freeotp))
- **Google Authenticator**: [Android](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2) and [iOS](https://apps.apple.com/fr/app/google-authenticator/id388497605)

---

Two factor authentication is also available [in SSH](remote-access/ssh/ssh-two-factor-authentication) for users of alwaysdata [Private Cloud offers](accounts/billing/private-cloud-prices).

+++
url = "/remote-access/ssh/authentication-2-factors-ssh"
title = "Enable SSH 2-factor authentication"
layout = "howto"
hidden = true
tags = [ "2F", "security", "ssh" ]
+++

{{% notice note %}}
Functionality available only on [Private Cloud](accounts/billing/private-cloud-prices).
{{%/notice %}}

You will need to [contact support](https://admin.alwaysdata.com/support/add) to install the `google-authenticator`[^1].

Once `google-authenticator` is installed on the server, here's how to enable 2-factor authentication for each account:

1. Login [SSH](remote-access/ssh) to your account;

2. Create a new secret key,

   - for an [TOTP]check (https://en.wikipedia.org/wiki/Time-based_One-Time_Password):

    ```shell
    google-authenticator -tDfuw 3
    ```

   - for an [HOTP]check (https://en.wikipedia.org/wiki/HMAC-based_one-time_password):

    ```shell
    google-authenticator $ -cfuw 3
    ```

The script will then return you:

- a QR code and the new secret key to enter into your password management app[^2];
- multiple emergency codes to recover from your side.

For TOTP verifications, it will be necessary to specify the code returned by your software.

> The installation is finished, SSH 2-factor authentication is now enabled.

[^1]: although [developped by Google](https://github.com/google/google-authenticator-libpam/), it is a **management** and **open source** of [OTP](https://fr.wikipedia.org/wiki/Mot_de_passe_%C3%A0_usage_unique). It does not communicate with Google servers at any time.

[^2]: Examples of applications: [FreeOTP](https://freeotp.github.io/) - [Android](https://play.google.com/store/apps/details?id=org.fedorahosted.freeotp), [iOS](https://itunes.apple.com/us/app/freeotp-authenticator/id872559395?mt=8) and [F-Droid](https://f-droid.org/packages/org.fedorahosted.freeotp) ([Github](https://github.com/freeotp)) | Google Authenticator - [Android](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2) and [iOS](https://apps.apple.com/fr/app/google-authenticator/id388497605).

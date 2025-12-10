+++
url = "/account/tokens/"
title = "Access Token Usage"
hidden = true
tags = [ "api", "profile" ]
+++

Tokens are identifiers used to authenticate a user or program calling our [API](api).

To manage it, go to the **Profile** menu.

{{< fig "images/profile-token.png" "Gear tokens">}}

It is necessary to have enabled [2 factor authentication](security/two-factor-authentication) to manage/modify its tokens.

{{% notice tip %}}
For even more security, manage one per app.
{{%/notice %}}

As with the admin interface you can only give access to [certain IP](security/ip-access-authorization).

They have the same [permissions](accounts/permissions) as the profile they are linked to.

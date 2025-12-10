+++
url = "/marketplace/ghost/"
title = "Ghost"
layout = "man"
hidden = true
tags = [ "cms" ]
+++

## Public cloud and disk space error

`ghost doctor`, which is launched during installations or updates, performs an unfunctional check on our Public Cloud.

Indeed, their [calcul](https://github.com/TryGhost/Ghost-CLI/blob/1c936d2a1a9816635e8202a136c8b9eac4a86dc6/lib/commands/doctor/checks/free-space.js#L9) of `system information` is incorrect and not compatible with our infrastructure. As it is not possible to disable this verification, add the `--categories --categories` options to the `ghost install` or `ghost update` commands to override the given template at `ghost doctor`.

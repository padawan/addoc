+++
url = "/guides/apache-pagespeed/"
title = "How to install Apache PageSpeed"
layout = "howto"
hidden = true
tags = [ "apache", "http", "application optimization", "site" ]
+++

[PageSpeed](https://www.modpagespeed.com/) automatically optimizes your website by modifying the resources on this web page to implement [best practices](https://developers.google.com/speed/docs/best-practices/rules_intro) web performance. **Apache mod_pagespeed** must be installed on the account.

Due to the special features of our infrastructure, their installation script is not usable on our servers, here are the steps to follow.

In our example, we use a [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- PageSpeed directory: `$HOME/pagespeed/`
- Apache 2.4

## Step 1: Downloading

```sh
foo@ssh:~/pagespeed$ wget https://dl-ssl.google.com/dl/linux/direct/mod-pagespeed-stable_current_amd64.deb
foo@ssh:~/pagespeed$ dpkg -x mod-pagespeed-stable_current_amd64.deb .
```

There are two modules, one for Apache 2.2 and the other for Apache 2.4.

## Step 2: Changing Apache Configuration

In **Web > Setup > Apache**, add:

```
LoadModule pagespeed_module "/home/[foo]/pagespeed/usr/lib/apache2/modules/mod_pagespeed_ap24.so"
ModPagespeedFileCachePath "/home/[foo]/pagespeed/cache/pagespeed/"
ModPagespeedFileCacheSizeKb 102400
ModPagespeedFileCacheCleanIntervalMs 3600000
ModPagespeedFileCacheInodeLimit 500000
```

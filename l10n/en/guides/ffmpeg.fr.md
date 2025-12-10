+++
url = "/guides/ffmpeg/"
title = "How to install FFmpeg"
layout = "howto"
hidden = true
+++

[FFmpeg](https://www.ffmpeg.org/) provides tools for processing audio or video streams.

This bibliotheque is a source of heavy processing and is not available by default on the Public Cloud.

{{% notice info %}}
If you own a [Private Cloud](accounts/billing/private-cloud-prices), contact our [support](https://admin.alwaysdata.com/support/add/). It will install it globally on the server.
{{%/notice %}}

In our example, we use [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- ffmpeg directory: `$HOME/ffmpeg/`

```sh
foo@ssh:~/ffmpeg$ wget https://johnvansickle.com/ffmpeg/releases/ffmpeg-release-amd64-static.tar.xz
foo@ssh:~/ffmpeg$ tar -xJf ffmpeg-release-amd64-static.tar.xz --strip-components=1
foo@ssh:~/ffmpeg$ rm ffmpeg-release-amd64-static.tar.xz
```

Binaries will be available in the `$HOME/ffmpeg/` directory.

Take the [latest stable amd64 release](https://johnvansickle.com/ffmpeg/).

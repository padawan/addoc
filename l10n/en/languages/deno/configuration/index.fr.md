+++
url = "/languages/deno/configuration/"
title = "Configure Deno"
hidden = true
layout = "man"
tags = [ "deno" ]
+++

## Supported Versions

|                      |
| -------------------- |
| 2.2  |
| 2.1  |
| 1.46 |
| 1.45 |
| 1.43 |

The default version can be changed in the alwaysdata administration, **Environment > Deno**. This version is especially used when you start `deno`.

Versions are not forcefully [already installed](languages#versions).

## Environments|Environment

Your Deno environment is initially empty, without any preinstalled libraries.

## HTTP Deployment

To deploy an HTTP application with Deno, create a _Deno_ site in the **Web > Sites** section.

{{< fig "images/deno.png" "Deno Site Type">}}

You will need to specify the command that starts your Deno application, for example:

```
deno run --allow-env --allow-net $HOME/myapp/index.ts
```

{{% notice warning %}}
Your app must not listen on the ip and port specified in the site configuration view under the _Command_ field. You can use the `IP` / `HOST` and `PORT` environment variables.
{{%/notice %}}

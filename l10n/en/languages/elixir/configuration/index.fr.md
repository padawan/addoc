+++
url = "/en/languages/elixir/configuration/"
title = "Configure Elixir"
hidden = true
layout = "man"
tags = [ "elixir" ]
+++

## Supported Versions

|                                                                                                                                                        |
| ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 1.13 \\| 1.14 \\| 1.15 \\| 1.16 \\| 1.17 \\| 1.18 |

The default version is editable in the administration, section **Environment > Elixir**. This version is especially used when you start `mix`.

Versions are not forcefully [already installed](languages#versions).

## Binary to use

To force a version of Elixir different from the default, define the `ELIXIR_VERSION` environment variable:

```sh
$ ELIXIR_VERSION=1.14 elixir
```

In your scripts, use `/usr/bin/elixir` as _shebang_:

```
#!/usr/bin/elixir
```

## Environments|Environment

Your Elixir environment is initially empty, without any preinstalled libraries.

## HTTP Deployment

To deploy an HTTP application with Elixir, create a _Elixir_ site in the **Web > Sites** section.

{{< fig "images/elixir.png" "Elixir Site Type">}}

You will need to specify the command that starts your Elixir application, for example:

```
mix $HOME/myapp/phx.server
```

{{% notice warning %}}
Your application must not listen on the `::` ip and port specified in the site configuration view under the _Command_ field; or use the IP and PORT environment variables.
{{%/notice %}}

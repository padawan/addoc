+++
url = "/languages/dotnet/configuration/"
title = "Set up .NET"
hidden = true
layout = "man"
+++

## Supported Versions

|                      |
| -------------------- |
| 10.0 |
| 8.0  |
| 6.0  |
| 5.0  |

The default version can be changed in the alwaysdata administration, **Environment > .NET**. This version is especially used when you start `dotnet`.

Versions are not forcefully [already installed](languages#versions).

{{% notice note %}}
Major versions of . AND alternate between LTS and Standard Term Support (STS) following [the lifecycle of their versions](https://dotnet.microsoft.com/en-us/platform/support/policy/dotnet-core#lifecycle). Only **LTS versions** are made available, and they are available once Microsoft supports General Availability (GA).
{{%/notice %}}

## Environments|Environment

Your .NET environment is initially empty, without any preinstalled libraries.

## HTTP Deployment

To deploy an HTTP application with .NET, create a _.NET_ site in the **Web > Sites** section.

{{< fig "images/net.png" ".NET Site Type">}}

You will need to specify the command that starts your .NET application, for example:

```
dotnet run --urls "http://$IP:$PORT"
```

{{% notice warning %}}
Your app must not listen on the ip and port specified in the site configuration view under the _Command_ field. You can use the `IP` / `HOST` and `PORT` environment variables.
{{%/notice %}}

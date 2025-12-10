+++
url = "/languages/lua/configuration/"
title = "Configure Lua"
hidden = true
layout = "man"
tags = [ "Lua" ]
+++

## Supported Versions

|                     |
| ------------------- |
| 5.4 |
| 5.3 |
| 5.2 |
| 5.1 |

The default version is Lua 5.4. This version is especially used when you start `lua`.

Versions are not forcefully [already installed](languages#versions).

## Binary to use

To use a different version of Lua than default, use `lua5.X`.

## Environments|Environment

[Luarocks](https://luarocks.org/) and [LuaJIT](http://luajit.org/) are preinstalled.

## HTTP Deployment

To deploy an HTTP application with Lua, create a _[User Program](sites/user-program)_ site in the **Web > Sites** section.

{{< fig "images/user-program.en.png" "User Program Site Type">}}

You will need to specify the command that starts your Lua application, for example:

```
lua5.1 $HOME/myapp/start-server.lua
```

{{% notice warning %}}
Your application must not listen on the `::` ip and port specified in the site configuration view under the _Command_ field; or use the IP and PORT environment variables.
{{%/notice %}}

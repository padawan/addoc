+++
url = "/en/languages/nodejs/configuration/"
title = "Configure Node.js"
hidden = true
layout = "man"
tags = [ "nodejs" ]
+++

`[paquet]` is to be replaced by the package name to install.

## Supported Versions

|    |
| -- |
| 24 |
| 22 |
| 20 |
| 18 |
| 16 |
| 14 |
| 12 |
| 10 |
| 8  |
| 6  |

The default version can be changed in the administration section **Environment > Node.js**. This version is especially used when you start `node`.

Versions are not forcefully [already installed](languages#versions).

{{% notice note %}}
Only **[LTS](https://nodejs.org/fr/about/previous-releases)** are made available.
{{%/notice %}}

## Binary to use

You should always use `node` (or `/usr/bin/node`). `nodejs` does not work.

To force a different version of Node.js than the default one, define the `NODEJS_VERSION` environment variable:

```sh
$ NODEJS_VERSION=12 node
```

In your scripts, use `/usr/bin/node` as _shebang_:

```
#!/usr/bin/node
```

## Environments|Environment

Your Node.js environment is initially empty, without any preinstalled libraries. You can use `npm` to install packages:

```sh
$ npm install [paquet]
```

You can also use `npm` in global mode, packages will be installed in the `$HOME/.npm-packages` directory:

```sh
$ npm install -g [paquet]
```

## HTTP Deployment

To deploy an HTTP application with Node.js, create a _Node.js_ site in the **Web > Sites** section.

{{< fig "images/nodejs.png" "Node.js Site Type">}}

You will need to specify the command that starts your Node.js application, for example:

```
$HOME/myapp/index.js node
```

{{% notice warning %}}
Your app must not listen on the ip and port specified in the site configuration view under the _Command_ field. You can use the `IP` / `HOST` and `PORT` environment variables.
{{%/notice %}}

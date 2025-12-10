+++
url = "/languages/go/configuration/"
title = "Configure Go"
hidden = true
layout = "man"
tags = [ "golang" ]
+++

## Version

Go being a compile language, it does not need to be special at alwaysdata for use. However, we offer version 1.22 which is used when you start `go`.

You can compile your programs elsewhere, for example locally.

## HTTP Deployment

To deploy an HTTP application with Go, create a _[User Program](sites/user-program)_ site in the **Web > Sites** section.

{{< fig "images/user-program.en.png" "User Program Site Type">}}

After compiling the program and loading it to your account, you will need to specify the command that starts your Go application, for example:

```
$ $HOME/myapp/hello
```

{{% notice warning %}}
Your app must not listen on the ip and port specified in the site configuration view under the _Command_ field. You can use the `IP` / `HOST` and `PORT` environment variables.
{{%/notice %}}

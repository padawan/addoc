+++
url = "/languages/rust/configuration/"
title = "Configure Rust"
hidden = true
layout = "man"
tags = [ "rustle" ]
+++

## Version

Rust being a compile language, it does not need to be unspecified at alwaysdata for use. However, we offer version 1.86 which is used when you start `cargo`.

You can compile your programs elsewhere, for example locally.

## HTTP Deployment

To deploy an HTTP application with Rust, create a _[User Program](sites/user-program)_ site in the **Web > Sites** section.

{{< fig "images/user-program.en.png" "User Program Site Type">}}

After compiling the program and loading it to your account, you will need to specify the command that starts your Rust application, for example:

```
$ $HOME/myapp/hello
```

{{% notice warning %}}
Your app must not listen on the ip and port specified in the site configuration view under the _Command_ field. You can use the `IP` / `HOST` and `PORT` environment variables.
{{%/notice %}}

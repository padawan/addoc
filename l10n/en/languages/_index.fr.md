+++
url = "/en/languages/"
title = "Languages"
pre = "<i class='fas fa-fw fa-code'></i> "
weight = 11
archetype = "chapter"
+++

Find all information about technologies powered by our servers:

- [.NET](languages/dotnet)
- [Deno](languages/deno)
- [Elixir](languages/elixir)
- [Go](languages/go)
- [Java](languages/java)
- [Lua](languages/lua)
- [Node.js](languages/nodejs)
- [PHP](languages/php)
- [Python](languages/python)
- [Ruby](languages/ruby)
- [Rust](languages/rust)

Other interpreters and languages can also be executed thanks to the [user program](sites/user-program).

## Versions

It is possible to choose a major version of a specific language or a minor version.

When the major versions are selected, the system automatically generates updates when a new minor version is released. This automatically checks for security and bug fixes, while maintaining full compatibility.

The versions used by default are those specified in the **Environment** menu of the admin interface. It is possible to choose another version using _Environment Variables_ (or for sites by choosing the version from **Web > Sites**).

### Private Cloud

Language versions are **automatically installed**, to limit disk space usage.[^1]

To execute the binary of a language (e.g. `python`), simply run `python`. This will internally call `/usr/bin/python`, which is a _wrapper_ to the "good" version of python (the one defined in its environment).

Binaries are stored in `/usr/alwaysdata/[langage]/[version]`. The directory of each version does not exist forcefully before calling the binary of the version in question, so you should not rely on `/usr/alwaysdata` to determine if a version is available but you can use:

```
$ alwrapper get_versions [langage]
```

[^1]: `[langage]` and `[version]` must be replaced by the language name / version.

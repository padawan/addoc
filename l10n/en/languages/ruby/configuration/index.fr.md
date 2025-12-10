+++
url = "/languages/ruby/configuration/"
title = "Configure Ruby"
hidden = true
layout = "man"
tags = [ "Ruby" ]
+++

`[paquet]` and `[version]` are to be replaced by the package name and version to install.

## Supported Versions

|                                                                                                                                                                                                    |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 3.4 \\| 3.3 \\| 3.2 \\| 3.1 \\| 3.0                                                                            |
| 2.7 \\| 2.6 \\| 2.5 \\| 2.4 \\| 2.3 \\| 2.2 \\| 2.1 \\| 2.0 |
| 1.9 \\| 1.8                                                                                                                                                       |

The default version can be changed in the administration section **Environment > Ruby**. This version is especially used when you start `ruby`.

Versions are not forcefully [already installed](languages#versions).

## Error logs

Ruby is running behind [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/), you can check the error logs in the `$HOME/admin/logs/uwsgi/[id]file. og`, or `[id]` is the identifier of your site, indicated in the **Web > Sites** section.

An excerpt of these logs is present in the alwaysdata administration interface (Logs - 📄).

## Binary to use

You should always use `ruby` (or `/usr/bin/ruby`). Never use `ruby2.4` or any other command.

To force a different version of Ruby than default, set the `RUBY_VERSION` environment variable:

```sh
RUBY_VERSION=2.3 ruby
```

In your scripts, use `/usr/bin/ruby` as _shebang_:

```
#!/usr/bin/ruby
```

To force a partial Ruby version:

```
#!/usr/bin/eval RUBY_VERSION=2.3 ruby
```

Other binaries included in Ruby (`gem`, `irb`, `ri`…) work in the same way.

## Environments|Environment

Your Ruby environment is initially empty, without any library preinstalled outside the standard library.

### Install Package

You can use `gem` to install packages:

```sh
$ gem install [paquet]
```

Packages are installed in the standard `$HOME/.gem` directory and are automatically added to the load path by Ruby.

Warning, you will need to reinstall the packages if you are switching to a major version of Ruby (2.3 and 2. are two major versions different, while 2.3.1 and 2.3.0 have the same major version).

You can specify a specific version:

```sh
$ gem install [paquet] -v [version]
```

### Uninstall Package

```sh
$ gem uninstall [paquet]
```

### Use Bundler

It is recommended to use [Bundler](http://bundler.io/) if you are using multiple separate Ruby apps, in such a way that each has its own isolated environment. Bundle installs packages listed in a _Gemfile_ file.

```sh
$ bundle install
```

## HTTP Deployment

For a Ruby application to be accessible through the web, you need to add a site in the **Web > Sites** section of the alwaysdata administration. We offer the **Ruby Rack** type that uses the web server [uWSGI](https://uwsgi-docs.readthedocs.io/en/latest/).

{{< fig "images/ruby-rack.png" "Ruby Rack Site Type">}}

- type: choose _Ruby Rack_;
- application path: the file path of your Rack application.

You can also fill in several optional fields:

- use Bundler;
- environment variables to be defined;
- a specific version of Ruby to use.

You can use another web server by launching it as a [User Program](sites/user-program).

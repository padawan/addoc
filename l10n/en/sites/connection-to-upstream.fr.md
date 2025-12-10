+++
url = "/sites/error-connection-to-upstream/"
title = 'Fix "Connection to upstream refused/skipped" errors'
layout = "howto"
hidden = true
tags = [ "http", "troubleshooting", "site" ]
+++

The **Connection to upstream refused** and **Connection to upstream skipped** errors indicate an issue when launching the application. This can either be the _HTTP server_ that fails to launch or the _application_ that is running but does not listen on the correct IP. Whatever the reason for more information are available in the `$HOME/admin/logs/sites` logs.

Here is a non-exhaustive list of examples:

## Apache

### Disk quota exceeded

```
=> Log sites for a site using Apache:
STDERR: (122)Disk quota exceeded: apache: could not open error log file /home/foo/admin/logs/apache/apache.log.

=> Apache Logs ($HOME/admin/logs/apache) :
[error] (122)Disk quota exceeded: Couldn't bind unix domain socket /home/foo/admin/config/apache/run/cgisoc
k. XXXXXX
[error] (122)Disk quota exceeded: could not create /home/foo/admin/config/apache/run/apache.pid
[error] apache: could not log pid to file /home/foo/admin/config/apache/run/apache.pid
```

Switch to the Superior Pack in the **Subscriptions** tab of your admin interface or delete files. This will mainly apply to free 100MB packs.

### Apache log not found

```
STDERR: (2)No such file or directory: apache: could not open error log file /home/foo/admin/logs/apache/apache.log.
STDERR: Unable to open logs
```

Try to restart the Apache instance (**Web > Sites > Reinitiate** a PHP site) to regenerate it or make a major change on one of the sites concerned (for example by adding a fictitious address).

### Parasitic Caract

```
STDERR: Syntax error on line XXX of /home/foo/admin/config/apache/sites. onf:
STDERR: Invalid command 'XXX', perhaps misspelled or defined by a module not included in the server configuration
```

Parasitic characters or directives that don't use the correct syntax have been added to the **Global Guidelines** field of a **custom Apache site**, in the **virtual host** field of the site concerned or in the Apache configuration (**Web > Configuration > Apache**). Correct or delete them.

{{% notice info %}}
There is only one Apache server per account, Prefer thus to manage [Apache directives](https://httpd.apache.org/docs/) at the virtual host or ` level. taccess` where possible.
{{%/notice %}}

## uWSGI

```
=> Logs sites :
STDERR: [uWSGI] getting INI configuration from /home/foo/admin/config/uwsgi/XXXXX.conf
Upstream starting failed: /usr/alwaysdata/uwsgi/2.0.17.1/bin/uwsgi --ini /home/foo/admin/config/uwsgi/XXXXX. onf (return code: 1 | reason: -)

=> uWSGI Logs ($HOME/admin/logs/uwsgi) :
chdir() to /home/foowww
chdir(): No such file or directory [core/uwsgi. line 2631]
-----
failed to open python file /home/foo/www/app. y
unable to load app 0 (mountpoint='') (callable not found or import error)
-----
unable to find "application" callable in file /home/foo/www/manage. y
-----
ModuleNotFoundError: No module named 'XXXX'
```

Depending on the error, correct the site, the virtual environment or the script itself.

For example, for a Python application (such as Django), check that the version in the virtual environment matches the version in the site (of the administration interface).

## Other HTTP servers

For sites not running Apache or uWSGI, please make sure to launch the [SSH]program (remote-access/ssh). Particularly if listening:

- to IPv6;
- on the given IP and port.

### Upstream not ready

```
Upstream starting failed: node ~/www/app.js (return code: - | reason: No such file or directory: '/www/')
```

The working directory specified in **Web > Sites** does not exist.

### Incorrect command (path)

```
STDERR: internal/modules/cjs/loader. s:589
STDERR: throw err;
STDERR: ^
STDERR: 
STDERR: Error: Cannot find module '/home/foo/www/app. s'
STDERR: at Function.Module._resolveFilename (internal/modules/cjs/loader.js:587:15)
STDERR: at Function.Module. load (internal/modules/cjs/loader.js:513:25)
STDERR: at Function.Module.runMain (internal/modules/cjs/loader.js:760:12)
STDERR: at startup (internal/bootstrap/node. s:308:19)
STDERR: at bootstrapNodeJSCore (internal/bootstrap/node.js:878:3)
Upstream starting failed: node ~/www/app.js
```

The file _/home/foo/www/app.js_ does not exist.

## Cannot parse upstream response

This error means that an HTTP response returned by your server/application is incorrect (malformed) and therefore our proxy cannot decrypt (and return it).

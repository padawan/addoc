+++
url = "/guides/mapserver/"
title = "How to use MapServer CGI"
layout = "howto"
hidden = true
tags = [ "http", "site" ]
+++

[MapServer](https://mapserver.org/) is a platform for publishing spatial data and interactive cartographic applications on the web.

In our example, we use a [SSH access](remote-access/ssh) and will have the following information:

- Account name: `foo`
- MapServer installation directory: `$HOME/mapserver`

1. Create symlink:

```sh
foo@ssh:~/mapserver$ ln -s /usr/lib/cgi-bin/mapserv
```

2. Create a `.htaccess` file containing:

```
Options +ExecCGI
SetHandler cgi-script
```

- [MapServer CGI](https://mapserver.org/cgi/)

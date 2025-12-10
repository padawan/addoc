+++
url = "/marketplace/odoo/"
title = "Odoo"
layout = "man"
hidden = true
tags = [ "Productivity" ]
+++

In our example, we will get the following information:

- Account name: `foo`
- Odoo directory: `$HOME/odoo/`
- Odoo HTTP Address: `foo.alwaysdata.net`
- Live Chat port: 8300 (ports between 8300 and 8499 can be used)

They will be modified according to your needs.

## Live Chat

After installing Odoo via our [marketplace](marketplace):

- In **Advanced > Services**, create the following [service](services) :

  - _Command_: `.venv/bin/python odoo-bin --config=.odoorc --http-port=8300 --proxy-mode`
  - _Work directory_: `/home/foo/odoo/`
  - _Environment_: `PYTHON_VERSION=3.10`

- In **Web > Sites**, declare an [site](sites/add-a-site) of type **Reverse proxy** with:

  - _Address_: `foo.alwaysdata.net/websocket/`
  - _Remote URL_: `services-foo.alwaysdata.net:8300`

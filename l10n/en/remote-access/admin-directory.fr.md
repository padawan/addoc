+++
url = "/remote-access/admin-directory/"
title = "Admin Directory: Presentation"
layout = "man"
hidden = true
tags = [ "account", "technical environment" ]
+++

Every account contains a `$HOME/admin` directory located at its root and accessible with [FTP](remote-access/ftp), [SSH](remote-access/ssh), [SFTP](remote-access/sftp) or [WebDAV](remote-access/webdav).

You will find in:

- _mail_ : mount [NFS](https://fr.wikipedia.org/wiki/Network_File_System) (Cloud Public) or a symlink (Private Cloud) of [emails](e-mails);
- _config_;
- _logs_;
- _tmp_ : stores temporary files from your applications (replacing /tmp);
- _backup_ : NFS mount of [sauvegardes](backups) which are therefore NOT stored locally.

{{% notice note %}}
This directory is NOT sent to your files.
{{%/notice %}}

## config

This directory hosts the Apache configuration files, uWSGI or languages. You can access it in **read-only**, with changes made directly to your alwaysdata admin interface, **Environment**, **Web > Configuration** or **Web > Sites**.

## logs

It collects different log types:

- _http_ : Access to your [sites web](sites);
- _sites_: launches, stops, and malfunctions of “upstream” web servers;
- _jobs_ : execution of your [scheduled tasks](tasks);
- _services_ : executing your [services](services);
- _apache_ : a log for all applications using this web server (custom PHP and Apache);
- _php_: A log for all applications using the PHP programming language;
- _uwsgi_ : a log for each application (Python WSGI, Ruby Rack and Ruby on Rails <= 2.x).

An excerpt of these logs is present in the alwaysdata admin interface (**Logs** - 📄).

{{% notice info %}}
A **delay period** of the logs can be set up for each account via the **Advanced> Logs** menu. For the Private Cloud, it is also possible to do this at the server level in its **HTTP** menu.
\*All logs (http, sites, jobs...) will be deleted once the desired period is passed. \*
{{% /notice %}}

Only the _apache_, _php_ and _uwsgi_ logs of the current month are included in an account's disk space quota.

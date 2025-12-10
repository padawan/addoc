+++
url = "/sites/fileer-htaccess/"
title = ".htaccess file"
layout = "man"
hidden = true
tags = [ "apache", "http", "site" ]
+++

`.htaccess` files are Apache configuration files. Here are some examples of the most common usage.

## Protect a directory with a password

Protect certain users with an identifier and a password to access files.

```
AuthName "Protected access"
AuthType Basic
AuthUserFile /path/absolute/to/.htpasswd
Require valid-user
```

The variable `$HOME` can be used to indicate the root of the account.

The `.htpasswd` file contains a list of authorized username/password pairs. It can be placed anywhere but must not be readable from the outside.

To create this `.htpasswd` file:

```sh
$ htpasswd -c .htpasswd <utilisateur>
```

By replacing `<utilisateur>` with the desired username. The tool requires you to enter the corresponding password twice.

## Limit access to a directory

Block access to a directory for a domain or IP. And vice versa, you can only allow access to the directory for the desired IPs and/or domains.

```
order deny,allow 
deny from all 
allow from <adresse IP / domaine>
require user <Login de l'utilisateur>
```

## Customize error messages (403, 404 ...)

The following syntax will define custom error pages:

```
ErrorDocument 403 /errorss/403.php 
ErrorDocument 404 /errorss/404.php
```

This syntax is valid regardless of [HTTP response code](http://fr.wikipedia.org/wiki/Liste_des_codes_HTTP).

## Redirect

This feature is available directly by declaring a site of type [Redirection](sites/redirect), but you can do it gracefully at the `.htaccess` file:

```
Redirect 301 <Fichier source> <Fichier destination>
```

You can also redirect an entire directory in this way:

```
RedirectMatch 301 <Répertoire source>(.*) <Répertoire destination>/$1
```

## URL Rewrite

The _URL rewrite_ (or URL Rewriting) is to modify the link structure. This practice is often used to improve indexing of your pages (and therefore referencing your site) by missing keywords in the addresses.

```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteRule ^(.*)$ {Fichier source}/$1 
```

## Possible errors

Any errors linked to `.htaccess` will be visible in the **$HOME/admin/logs/apache/apache.log\`**.

```
Invalid command '\xef\xbb\xbf', maybe misspelled or defined by a module not included in the server configuration
```

The `.htaccess` file was not saved in the correct format. Please be careful to save your file without [BOM](http://fr.wikipedia.org/wiki/Indicateur_d%27ordre_des_octets). This is usually an option from your editor.

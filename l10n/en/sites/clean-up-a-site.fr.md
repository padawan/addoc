+++
url = "/sites/desinfecter-un-site/"
title = "How to un-infect a website"
linkTitle = "Un-infect a site"
layout = "howto"
weight = 90
tags = [ "Infection", "malware", "spam" ]
+++

Infection of a site can result in different hands:

- sending spam;
- malware attacking other servers;
- phishing;
- redirect to a third party site.

When alwaysdata support detects an infection it will block the malware and contact the user to do the necessary thing.

The vast majority of attacks are done by automated scripts. It is therefore not recommended to reinstall the site and its extensions in the same condition on pain of suffering a new infection within hours. Here are the actions to be taken then:

## 1. Delete infected files

The following commands, presented for a site using PHP, are executed via [SSH](remote-access/ssh) in the directory of your site.

- Make sure that redirects or other directives have not been added to your knowledge by controlling the content of your `.htaccess` files. There should be only one, located at the root of your site:

    ```sh
    $ find . -type f -name .htaccess
    ```
- Browse your files for [malwares](http://fr.wikipedia.org/wiki/Logiciel_malveillant):

    ```sh
    $ find . -type f -name "*.php" | xargs grep base64_decode
    ```

    ```sh
    $ find . -name "*.php" | xargs grep eval
    ```

L'infection se présente comme une suite alphanumérique exécutée avec la fonction PHP [eval](http://www.php.net/manual/fr/function.eval.php) :

```php
eval(gzinflate(base64_decode("FZy3sqMKFkX/ZaL3igDvaiI8QngPyRTee8/Xj24n3UFfCcE5e6+li1ScSf9P9TZjj2Sd78U+abAWB/S8vsikv/vmPGL9ie7zfvQtBPE2Nzt4HaPd3Q0M1RB6eMYgHwFxCOF+T7/ppow3C7Tl5m9bcQWIs4uYlcw4Envy7f1QeBO4UpzkUACLAO8UvWkhraTMMWF5rcCGA10u37A0klvx9Gzqt
```

This base64-encoded sequence is simply a PHP script that will be executed when the page is called.
So you can decode this suite to understand what the hacker is trying to do:

```php
echo gzinflate(base64_decode("FZy3sqMKFkX/ZaL3igDvaiI8QngPyRTee8/Xj24n3UFfCcE5e6..."));
```

Or then:

```sh
$ find . -name "*.php" -print0 | xargs -0 grep eval
```

```php
$sF="PCT4BA6ODSE_";$s21=strtolower($sF[4].$sF[5].$sF[9].$sF[10].$sF[6]...
```

```php
$qV="stop_";$s20=strtoupper($qV[4].$qV[3]...
```

All these files must be **deleted**.

- Check your sources for hidden folders that contain a copy of previously deleted malware:

    ```sh
    $ find . -type d -name ".*"
    ```

- List the modified files in the last 24 hours (1 having the number of days):

    ```sh
    $ find . -type f -mtime -1 -print
    ```

- Check your database integrity by browsing the latest records.

## 2. Failure search

Depending on the creation date of the files, their name and call, it is possible to find the permissive URL called.
To do so, check for POST requests from your Apache logs located in the `$HOME/admin/logs/http` directory:

```sh
$ grep POST $HOME/admin/logs/http/[année]/http-[date].log[.gz]
```

Sample suspicious calls:

```
domain.tld 37.139.47.91 - [23/Nov/2013:09:13:37 +0100] "POST /wp-content/themes/twentythirteen/404.php?pwd HTTP/1.0" 200 4598 "-" "Mozilla/5.0 
domain.tld 81.27.32. 47 - [23/Nov/2013:03:19:16 +0100] "POST //wp-content/themes/lightspeed/framework/_scripts/valums_uploader/php.php HTTP/1. " 200 100 "-" "-"
domain.tld 31.184.244.18 - [31/May/2013:02:12:37 +0200] "POST /templates/beez/7c31.php HTTP/1.1" 200 - "-" "-"
```

The name of the files, POST calls on URLs that do not contain treatments, are hints that allow you to go back to the first HTTP request that is the source of the infection.

{{% notice tip %}}
If the infection is **was** and the search for the complicated infection, it is possible to restart an [sauvegarde](backups).
{{%/notice %}}

## 3. Remove infection vectors

- **Update application** and its plugins and themes;

- Delete all inactive plugins and themes;

- Find out about bug reports and security vulnerabilities of applications/plugins before installing them;

- Set up the [web application firewall](sites/waf);

- Change the prefix of your database tables names (e.g. for WordPress _wp\__);

- Delete the readme.txt file from the root of your application;

- Delete users created by default;

- Protect yourself from [hotlinking](http://fr.wikipedia.org/wiki/Hotlinking) by adding to the .htaccess file:

    ```
    # Enable Rewrite Mode
    RewriteEngine on
    RewriteCond %{HTTP_REFERER} ! $
    
    # Requests from your domain are allowed
    RewriteCond %{HTTP_REFERER} !^http(s)?://(www\. ?your domain. om [NC]
    
    # Permission to use content by
    RewriteCond %{HTTP_REFERER}  ! earch\?q=               [NC]
    RewriteCond %{HTTP_REFERER}  !google\.                      [NC]
    
    # Referring an alternative image in case of misuse of your
    RewriteRule \. gif|jpg|png)$ http://domain.tld/hotlink.jpg [R,NC,L]
    ```

- other XSS filtering redirects, HTTP redirects, and PHP variable changes:

    ```
    RewriteEngine On
    RewriteCond %{REQUEST_METHOD} (GET|POST) [NC]
    RewriteCond %{QUERY_STRING} ^(.*)(%3C|<)/?script(. )$ [NC,OR]
    RewriteCond %{QUERY_STRING} ^(.*)(%3D|=)?javascript(%3A|:)(.*)$ [NC,OR]
    RewriteCond %{QUERY_STRING} ^(.*)document\.location\.href(. )$ [OR]
    RewriteCond %{QUERY_STRING} ^(.*)base64_encode(.*)$ [OR]
    RewriteCond %{QUERY_STRING} ^(.*)GLOBALS(=|%[0-9A-Z]{0,2})(. )$ [OR]
    RewriteCond %{QUERY_STRING} ^(.*)_REQUEST(=|%[0-9A-Z]{0,2})(.*)$ [OR]
    RewriteRule (.*) - [F]
    ```

---

## Links

- [Sucuri](http://sucuri.net/): scans and identifies potential vulnerabilities in your site;
- [Google Webmaster Tools](https://www.google.com/webmasters/tools/home): Provides detailed reports on the visibility of your site.


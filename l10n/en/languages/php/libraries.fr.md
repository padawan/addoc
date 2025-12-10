+++
url = "/en/languages/php/add-une-bibliotheque/"
title = "How to add a PHP library"
hidden = true
layout = "howto"
tags = [ "php" ]
+++

Changing a file in `/etc/ld.so.conf.d` changes the global configuration of the system, not compatible with the alwaysdata infrastructure.

There are two solutions:

- set environment variable `LD_LIBRARY_PATH`, which would then be `/home/[compte]/[bibliothèque]`[^1]. It can be complex to ensure that it is defined in all cases.

- modify the path of the rpath directly in the `.so` file with the command:

```sh
$ chrpath -r /home/[compte]/[bibliothèque]/ ~/[bibliothèque]/[bibliothèque].so
```

Whenever this file is loaded, the `/home/[compte]/[bibliothèque]/` directory will be used to resolve the dependencies.

It will remain to add the path to `.so` in the `php. ni` via the **Environment** menu (or in **Web > Sites** in the case of a custom `php.ini`.

[^1]: [compte] and [bibliothèque] must be replaced by their names.

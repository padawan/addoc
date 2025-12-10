+++
url = "/marketplace/wordpress/"
title = "WordPress"
layout = "man"
hidden = true
tags = [ "cms", "wordpress" ]
+++

- [Enable HTTP Cache on WordPress](sites/activate-http-cache-on-wordpress)

## Migration from another hosting provider

You will need to edit:

- _siteurl_, _home_ settings in the `_options` table of the database;
- file `$HOME/path/to/application/wp-config.php` (located at the root of the application).

## Recommendations

Its notoriety made it a priority target for hackers, so it is important to follow these few usage recommendations:

- update updated _WordPress_ and its plugins;

- investigate bug reports and security vulnerabilities of plugins before installing them;

- set up the [specific profile](sites/waf#profils-disponibles) of our WAF;

- choose a prefix other than _wp__ for the names of your tables. To change this value on a WordPress already deployed, edit the `_options` table and the `$HOME/path/to/application/wp_config.php` file.

- remove inactive themes and plugins;

- delete the readme file. xt at the root of your application (contains the current version of your WordPress, useful for knowing exploitable security vulnerabilities);

- edit the `$HOME/path/to/application/wp-content/themes/theme/functions.php` file and add:

    ```php
    remove_action("wp_head", "wp_generator");
    ```

  This will hide the version number in the meta name generator. Add:

    ```php
    add_filter('login_errors',create_function('$a', "return null;"));
    ```

  To hide login errors.

- delete default created "admin" account;

- of [other things](sites/clean-up-a-site#3-supprimer-les-vecteurs-dinfection).

---

## Useful links

- [iThemes Security](http://wordpress.org/plugins/better-wp-security/): Improve the security of your WordPress site
- [WordFence](https://wordpress.org/plugins/wordfence/): scans your site for vulnerability, WAF and other security tools for your WordPress interface

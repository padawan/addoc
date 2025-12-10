+++
url = "/marketplace/creer-script-dapplication/"
title = "Create own app script"
layout = "man"
hidden = true
+++

Any user can propose a script in the _language of their choice_ that will allow users to install their application. This script will be executed with the _rights of the account on which the installation occurs_ and must start with a YAML comment.

{{< fig "images/create-script.en.png" "Create Application Script" >}}

Scripts consist of two parts:

- the YAML **dataset** which allows you to configure the site and ask the user for the information necessary for the script (the `FORM_*` variables). It can be divided into four :
  - **site** : see the [API documentation](https://api.alwaysdata.com/v1/site/doc/) that uses all possible options.
  - **database** : mysql, postgresql, couchdb, rabbitmq.
  - **requirements**: Specify blocking conditions that may be problematic on certain hosting planes/packs.
  - **form**: all variables requested by the user creating the site. Example: Site title, Administrator ID, Email Address, Administrator First Name...
- the **script** itself

## Environment Variables

| Variables                                                       | Description                                                                                                                                   | Example                                                    |
| --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------- |
| USER                                                            | Account Name                                                                                                                                  | `foo`                                                      |
| HOME                                                            | Account Root for Script                                                                                                                       | `/home/foo/example/`                                       |
| NAME_APP                                   | App name                                                                                                                                      |                                                            |
| INSTALL_URL                                | Site Address                                                                                                                                  | `foo.example.net/test`                                     |
| INSTALL_URL_PATH      | Site Root (base URL)                                                                                                       | `/test`                                                    |
| INSTALL_URL_HOSTNAME  | Site Host Name                                                                                                                                | `foo.example.net`                                          |
| INSTALL_PATH_RELATIVE | Relative path from account root (no slash final)                                                                           | `example`                                                  |
| INSTALL_PATH                               | Absolute path (without trailing slash)                                                                                     | `/home/foo/example`                                        |
| DATABASE_USERNAM                           | Database login user (automatically managed)                                                                                | `foo_*`                                                    |
| DATABASE_PASSWORD                          | Password of the user login to the database (automatically managed)                                                         |                                                            |
| DATABASE_NAME                              | Site Database (automatically managed)                                                                                      | `foo_*`                                                    |
| DATABASE_HOST                              | Host name to connect to the database server                                                                                                   | `mysql-foo.alwaysdata.net` (MySQL base) |
| SMTP_HOST                                  | Host name to connect to the mail server                                                                                                       | `smtp-foo.alwaysdata.net`                                  |
| RESELLER_DOMAIN                            | Root-Domain used by host                                                                                                                      | `alwaysdata.net`                                           |
| FOR_\*                                     | Other variables explicitly requested from the user in the "form" section of the YAML dataset                                                  |                                                            |
| PORT                                                            | Specific port for User Program, Node.js, Elixir, .NET and Deno sites                                          |                                                            |
| `::` or IP                                                      | Specific IP for User Program, Node.js, Elixir, .NET and Deno sites (preferring `::` to IP) |                                                            |

If other variables are needed, open a [support ticket](https://admin.alwaysdata.com/support/add/).

### Notes and hints

- The script must start with `set -e` to stop it when it fails;
- Specify the **language version** (PHP, Python, Ruby, Node. s and Elixir) is preferred to avoid depending on the default account configuration;
- The root directory specified by the user (`INSTALL_PATH`) is the root directory for the script (a `export HOME=` is executed by default);
- To make a install script public you must specify the `disk` condition of the `requirements`;
- It is preferable to request a minimum amount of information to avoid making the script complete. _Users will be able to change their application configuration laterally._
- To add a **optional** form field, set the `required` option to `false`. If the user does not specify anything the field will remain empty;
- The _labels_ and _regex_text_ are translatable. Depending on the language chosen on its alwaysdata administration interface, the user can have the form questions in the specified languages.

{{% notice note %}}
To make its script accessible to users of the alwaysdata platform, it is necessary to check the box to make it _public_. **Any script marked as public must be maintained and will be at least verified by the alwaysdata team.**
{{% /notice %}}

{{% notice tip %}}
A _URL of a time_ can be specified to facilitate maintenance. In this case, Once the changes have been pushed to the current time, the application has only to be updated via the previewed button to this effect.
{{%/notice %}}

## Example - Drupal installation script

```
#!/bin/bash

# Declare site in YAML, as documented on the documentation: https://help.alwaysdata.com/en/marketplace/build-application-script/
# site:
#     type: php
#     path: '{INSTALL_PATH_RELATIVE}/web'
#     php_version: '8.3'
# database:
#     type: mysql
# requirements:
#     disk: 140
# form:
#     language:
#         type: choices
#         label:
#             en: Language
#             fr: Langue
#         choices:
#             de: Deutsch
#             en: English
#             es: Español
#             fr: Français
#             it: Italiano
#     site_name:
#         label:
#             en: Site name
#             fr: Nom du site
#         max_length: 255
#     email:
#         type: email
#         label:
#             en: Email
#             fr: Email
#         max_length: 255
#     admin_username:
#         label:
#             en: Administrator username
#             fr: Nom d'utilisateur de l'administrateur
#         regex: ^[ a-zA-Z0-9.@_-]+$
#         regex_text:
#             en: "It must include at least 5 characters which can be uppercase, lowercase, numbers, spaces, and special characters: .@_-."
#             fr: "Il doit comporter au moins 5 caractères qui peuvent être des majuscules, des minuscules, des chiffres, des espaces et les caractères spéciaux : .@_-."
#         min_length: 5
#         max_length: 255
#     admin_password:
#         type: password
#         label:
#             en: Administrator password
#             fr: Mot de passe de l'administrateur
#         min_length: 5
#         max_length: 255

set -e

# https://www.drupal.org/docs/system-requirements

# Download & install dependancies
COMPOSER_CACHE_DIR=/dev/null composer2 create-project drupal/recommended-project

cd recommended-project

sed -i "/\"require\": {/a \ \ \ \ \ \ \ \ \"drush/drush\": \"^12.1\"," composer.json

COMPOSER_CACHE_DIR=/dev/null composer2 update

# Install
# CLI: https://drushcommands.com
echo "y" | php vendor/drush/drush/drush.php si --db-url=mysql://"$DATABASE_USERNAME":"$DATABASE_PASSWORD"@"$DATABASE_HOST"/"$DATABASE_NAME" --account-name="$FORM_ADMIN_USERNAME" --account-pass="$FORM_ADMIN_PASSWORD" --account-mail="$FORM_EMAIL" --site-name="$FORM_SITE_NAME" --locale="$FORM_LANGUAGE"

# Handle subdirectories base URL
if [ "$INSTALL_URL_PATH" != "/" ]
then
    sed -i "s|# RewriteBase /$|RewriteBase $INSTALL_URL_PATH|" web/.htaccess
fi

# Clean install environment
cd
rm -rf .config .local .subversion
shopt -s dotglob
mv recommended-project/* .
rmdir recommended-project
```

The `disk:140` condition provides that installing Drupal requires 140 MB of disk space. The free offer is therefore too fair.

Use the `regex_text` condition to explain `regex` with words.

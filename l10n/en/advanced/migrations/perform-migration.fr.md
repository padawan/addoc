+++
url = "/avance/migrations/effectuer-une-migration/"
title = "How to migrate"
layout = "howto"
hidden = true
tags = [ "infrastructure", "migration" ]
+++

Each migration enhances changes that may cause incompatibilities with your applications. This is why we advise you to be very vigilant when performing a migration, especially since it is not possible to go back.

## 1. Read the documentation

Each migration is written in a page of our documentation. Read it carefully: the most important incompatibilities will be indicated.

## 2. Check the compatibility of your applications

You may need to intervene on your applications to keep them running after migration. For example, for a migration to a newer version of MySQL, you may need to change some SQL requests.

## 3. Prepare Migration

Before performing the migration you will be able to perform a certain number of actions. This allows you to ensure that your applications will continue to work, and fix them otherwise.

### Test databases

**Some** migrations can be tested by using a **Tester** button. This will attempt to import your account databases into a temporary server using new versions.

## 4. Migrate

Once you test the migration and make sure everything works properly, you can run the migration again. During migration, your account may be unavailable for a short duration (seconds or minutes, depending on your account data). _You don't need to stop your sites or databases: we take care of everything.

It is possible to perform a _temporary_ backlog if you have any problems. This backlog is possible for 7 days after the migration starts.

- [Private Cloud Migration Specification](advanced/migrations/private-cloud-migrations)

+++
url = "/en/languages/php/frequent-issues/"
title = "PHP - Frequent Issues"
layout = "man"
hidden = true
tags = [ "troubleshooting", "php" ]
+++

## mod_fcgid: can't apply process slot

This error message returned by the Apache log (`$HOME/admin/logs/apache/`) indicates that the limit on the number of PHP processes (_20_) at a moment T has been reached and new connections are waiting for a PHP process to be available.

To quickly restart the site you can restart it in **Web > Sites**. However, this will only "artificially" and temporarily fix the problem. You can [parse processes](sites/analyze-processes) or use PHP profiling services such as [New Relic](https://newrelic.com/products/application-monitoring), [Tideways](https://tideways.com/) or [Blackfire](https://blackfire.io/) to find the source.

There may be many reasons: lack of optimization, external resource unreachable, session problem...

### Sessions blocked

Whenever a PHP session is started, a file is created (`session.save_path`) containing all its information and assigning an ID to it. When a user returns it will provide this ID that will allow `session_start()` to recover its session data. Whenever `session_start()` is started the session file is locked using `flock`.

This may cause problems when two PHP processes attempt to access the same PHP session simultaneously: the second one will have to wait until the first one finishes to execute to avoid competitive incidents. This resulted in delays and even unavailability.

Parsing your HTTP processes return:

```sh
$ strace -f -p1821543 -p1822026 
Process 1821543 attached
Process 1822026 attached
[pid 1821543] flock(8, LOCK_EX <unfinished ...>
[pid 1822026] flock(8, LOCK_EX
```

{{% notice tip %}}
You will find on this [documentation](https://ma.ttias.be/php-session-locking-prevent-sessions-blocking-in-requests/) more information and solutions to fix these troublesome sessions. The best practice, allowing to limit the time during which the session is blocked, is to call `session_start()` as late as possible and `session_close()` as soon as possible.
{{%/notice %}}

In case of _necessary_, it is possible to set the configuration option `session.disable_locking` to `1` to remove any possibility from _lock_. **WARNING**, this can **corrupt sessions** and therefore complicate each other.

## Error messages

### Fatal error: Allowed memory size of 268435456 bytes exhausted

You reach the 256MB limit, default value of `memory_limit` in PHP. You can increase this value via `php. ni` in **Environment > PHP** or at the site level in **Web > Sites > Edit [site] - ⚙️**.

## Use different SSH versions

To use in SSH a different PHP version and/or PHP configuration than the one specified in **Environment > PHP**, it is possible to use the following commands:

```sh
$ export PHP_VERSION=<version>
$ export PHPRC=/path/to/php.ini
```

or for the `php.ini`:

```sh
$ php -c /path/to/php.ini
```

`php.ini` files are read-only available in the `$HOME/admin/config/php/` directory.

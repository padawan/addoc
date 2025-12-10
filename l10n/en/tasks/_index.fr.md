+++
url = "/en/project-planning/"
title = "Scheduled tasks"
pre = "<i class='fas fa-fw fa-stopwatch'></i> "
weight = 32
layout = "man"
tags = [ "scheduled tasks" ]
+++

Web apps or services sometimes need to execute tasks in the process, to execute tasks or to execute common functions or URLs, without any useful interaction. To do this, you have to create a job placed.

Our layout is based on [Debian](https://www.debian.org/) and its [crontab](https://fr.wikipedia.org/wiki/Cron) but allows you to manage them directly in our [administration interface](https://admin.alwaysdata.com) - tab **Advanced > Planned Tasks** - and make it easier to use.

Several types of information are to be provided:

- the order(s) you want to execute, or the URLs you want to request. Email addresses can also be provided to receive error reports[^1] (separated by a space).

{{< fig "admin-panel_create-task_type.en.png" "" >}}

- SSH environment

{{< fig "admin-panel_create-task_environment.en.png" "" >}}

- the duration of your task: you can specify a fixed time, or an interval

{{< fig "admin-panel_create-task_frequency.en.png" "" >}}

- [API Reference](https://api.alwaysdata.com/v1/job/doc/)

## Use scheduled tasks

- If the task is programmed at a certain frequency, but the execution of the previous task is not completed, the current will be ignored;
- Tours are started in the minute indicated. In other words, a job to start daily at 6:30, will start between 6:30:00 and 6:30:59;
- A log is automatically created and available in the `$HOME/admin/logs/jobs/` directory. It gives you the start and stop of the job.
  - An excerpt of these logs is present in the alwaysdata admin interface (**Logs** - :page_facing_up));
  - email addresses provided to receive error reports do not replace these logs;
- Ongoing processes can be accessed via the **Advanced> Process > Scheduled Tasks**;
- For _Command_ type tasks, the language versions used by default are those specified in the **Environment** menu of the admin interface. It is possible to choose another version using _Environment Variables_.

{{% notice note %}}
If your script needs to authorize certain IPs, allow these [IP address ranges](security/ip-ranges).
{{%/notice %}}

[Public Cloud](accounts/billing/public-cloud-prices):

- Consumption must remain reasonable. If the scheduled task is a heavy treatment, the frequency should be reduced.

[Private Cloud](accounts/billing/private-cloud-prices):

- Meme if this is contraindicated, access to the `crontab -e` command is also available. The two systems are distinct.

## Frequent Issues

- `source venv/bin/activate && python` is specific to [Bash](https://fr.wikipedia.org/wiki/Bourne-Again_shell) and cannot work. Replace with `venv/bin/python`;
- shortcuts in **@** - examples _@hourly_ or _@reboot_ - are not accepted (non-normalized syntax).

## Examples

### WordPress

Launch the [WordPress]tool (https://developer.wordpress.org/cli/commands/cron/event/run/) every ten minutes to perform their scheduled tasks:

Alwaysdata admin interface:

- _value_ : `php $HOME/wordpress/htdocs/wp cron event run --due-now`
- _frequence_ : second choice - Every 10 minutes

Compatible crontab syntax:

```
*/10 * * * * php $HOME/wordpress/htdocs/wp cron event run --due-now
```

### tt-rss

[Refresh an RSS backend](https://git.tt-rss.org/fox/tt-rss.wiki.git/tree/UpdatingFeeds.md#n58) with TT-rss, every day at 1030:30:

Alwaysdata admin interface:

- _value_ : `php $HOME/tt-rss/update.php --feeds --quiet`
- _frequence_ : first choice - Every day at 10:30

Compatible crontab syntax:

```
30 10 * * * php $HOME/tt-rss/update.php --feeds --quiet
```

[^1]: A report is sent when the return code is different from 0. If the job is not executed, no mail is sent.

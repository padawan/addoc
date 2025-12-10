+++
url = "/sites/analyser-des-processus/"
title = "How to parse HTTP processes"
layout = "howto"
hidden = true
tags = [ "http", "troubleshooting", "site" ]
+++

This feature allows developed developers to observe the behavior of their applications and improve their performance.

Process analysis produces a file, available at the root of your account (named `analysis_[date]-[heure]. og` and viewable in [SSH](remote-access/ssh) or [FTP](remote-access/ftp)) describing the processes executed during a hard process.

## 1. Start Analysis

{{< fig "images/admin-panel_processes-list.png" "Process Menu: List" >}}
{{< fig "images/admin-panel_processes-analysis.png" "Analyze processes" >}}

- _PIDs_ : list of process PIDs to listen, separated by a space.  If this field is empty, all HTTP request response processes will be parsed.
- _Scan Hard_ : Once the scan is launched, it will last for the specified time (in seconds). Geometrically, 30 to 60 seconds is sufficient. Analysis only works if pages on your site are displayed, so you have to leave some time to display some pages. but avoid saving too many data that may complicate reading of the result.
- _Interpret_ : by default, the result of the analysis matches the result of a call to `strace` [^1], which can be difficult to read. If this option is enabled, the result will be interpreted and filtered.
- _Slow OPERations_ : by enabling this option, only the slower or larger OPERations (during at least 1ms) will be displayed.

Once the scan is started, simply consult the pages you want to watch from your browser, during the hard scan process.

{{% notice note %}}
The PID of a process is displayed in the process board displayed in the **Advanced> Process** menu.  Sometimes no processes are visible in this array. They will appear if you visit a few pages of your website.
{{%/notice %}}

{{% notice warning %}}
The file produced by the scan may contain sensitive data, such as passwords. It is advisable to remove it.
{{%/notice %}}

## 2. Understand Results

The contents of the file containing the results of the analysis contain one row per row, such as these (shortcuts and truncated for readability):

```
5857 16:16:57.265015 0. 29 ms Send data (MySQL) ("SELECT * FROM posts
                              WHERE posts. ost_type = 'page' ORDER BY
                              posts. ost_date DESC".. )
5857 16:16:57.265105 53 ms Wait until being able to receive data (MySQL)
```

These lines contain the PID of the process that performed the process, the time at which it was executed, its hardness and operation.

Here we can see that an SQL request has been sent to a MySQL server. Sending request took only 0. 29ms, which is fast treble but the following line shows that it took 53ms before the MySQL server was ready to send the response, This is much less so.

{{% notice note %}}
Not all results are so obvious : often, Even if no operage is really slow, it is their large number that makes the site slow. In this case, it is necessary to restart the scan by turning off the **Slow Options** filter.
{{%/notice %}}

## Imprecise OPERations

It may happen that the analysis of a process begins when the process was already responding to an HTTP request. The analysis tool will not be able to accurately interpret the changes made for the current request. It is better, in this case, to look for the start of a next request. They are repainted using a line like this:

```
73510 16:53:04.551317 1.08 s Wait for incoming connection from socket...
```

[^1]: More information on [the strace tool](https://fr.wikipedia.org/wiki/Strace).

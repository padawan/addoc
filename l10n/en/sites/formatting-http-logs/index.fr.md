+++
url = "/sites/formater-les-logs-http/"
title = "Format HTTP logs"
layout = "man"
hidden = true
tags = [ "http", "site" ]
+++

Go to the **Logs** tab of your site (menu **Web > Sites**) to customize HTTP access logs; then stored in the `$HOME/admin/logs/http/` directory.

{{< fig "images/admin-panel_add-site-logs_standard.png" "" >}}

## Format types

- _Standard_[^1] format:

```txt
{request_hostname} {client_ip} - [{completion_date:%d/%b/%Y:%H:%M:%S %z}] "{request}" {status} {response_size} "{referer}" "{user_agent}"
```

> Example:

```sh
blog.alwaysdata.com 198.51.100.42 - [17/Feb/2022:14:19:01 +0100] "GET /2022/02/01/2022-au-rapport / HTTP/2.0" 200 16634 "https://blog.alwaysdata.com/" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:96.0) Gecko/20100101 Firefox/96.0"
```

- _Advance_ format (default format):

```txt
{request_hostname} {client_ip} - [{completion_date:%d/%b/%Y:%H:%M:%S %z}] "{request}" {status} {response_size} "{referer}"{user_agent}" {protocol} {duration}
```

> Example:

```sh
blog.alwaysdata.com 198.51.100.42 - [17/Feb/2022:14:19:01 +0100] "GET /2022/02/01/2022-au-rapport / HTTP/2.0" 200 16634 "https://blog.alwaysdata.com/" "Mozilla/5.0 (X11; Ubuntu; Linux x86_64; rv:96.0) Gecko/20100101 Firefox/96.0" https 0.128109
```

{{% notice tip %}}
To extract long requests, use the following command: `awk '{print $NF,$0}' $HOME/admin/logs/http/[année]/[fichier]. og | spell -n | cut -f2- -d' '`
{{% /notice %}}

- the _Custom_ format. The format of the log lines is customised in the **Format** field. This field accepts character chains and a number of variables listed below.

{{< fig "images/admin-panel_add-site-logs_custom.png" "" >}}

The syntax to follow is `{nom_de_variable}` to see its value appear in access log rows.

### Available variables

| Variables                               | Description                                                                                                                         |
| --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| {client_ip}        | IP address of the user who issued the request                                                                                       |
| {completion_date}  | Date the request was served [^2]                                                                                                    |
| {duration}                              | Time taken to serve the request in seconds                                                                                          |
| {peer_ip}          | IP address of peer that sent request (proxy or original user in case)                                            |
| {protocol}                              | Request protocol mechanism (http, https, ws)                                                                     |
| {referer}                               | [`Referer`](https://developer.mozilla.org/fr/docs/Web/HTTP/Reference/Headers/Referer) header value transmitted by request           |
| {request}                               | Request first line                                                                                                                  |
| {request_header}   | Request Headings [^3]                                                                                                               |
| {request_hostname} | Host name requested in request                                                                                                      |
| {request_method}   | Method used in request (GET, POST, ...)                          |
| {request_path}     | Requested path in the request, including question chain                                                                             |
| {request_protocol} | Protocol used in request (HTTP/1.1, HTTP/2, ...) |
| {request_time}     | Date the request was retrieved [^2]                                                                                                 |
| {response_header}  | Answers [^3]                                                                                                                        |
| {response_size}    | Response size in bytes, excluding HTTP                                                                                              |
| {ssl_version}      | Protocol version used for SSL connection                                                                                            |
| {status}                                | Response Status Code (200, 301, 404, 500, ...)                   |
| {user_agent}       | [`User-Agent`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Reference/Headers/User-Agent) header value transmitted by request  |
| {username}                              | Username specified in header [`Authorization`](https://developer.mozilla.org/fr/docs/Web/HTTP/Reference/Headers/Authorization)      |

## Specific cases

To display a user's IP behind [Cloudflare](https://support.cloudflare.com/hc/en-us/articles/200170986-How-does-Cloudflare-handle-HTTP-Request-headers-) use `{request_header:cf-connecting-ip}`.

[^1]: [Combined Log Format with vhosts](https://httpd.apache.org/docs/2.4/logs.html)

[^2]: Can be formatted by following syntax [strftime](https://docs.python.org/fr/3.6/library/datetime.html?highlight=strftime#strftime-strptime-behavior).
    _Examples: `{completion_date:%d/%b/%Y}` → 16/Jul/2018, `{completion_date:%H:%M:%S}` → 12:04:07_

[^3]: A single header can be specified. Examples: `{request_header:authorization}`, `{response_header:age}` (used with [HTTP cache](sites/http-cache))

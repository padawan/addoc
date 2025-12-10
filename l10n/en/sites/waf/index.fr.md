+++
url = "/sites/waf/"
title = "Web Application Firewall (WAF)"
linkTitle = "WAF"
weight = 60
layout = "man"
tags = [ "http", "site", "waf" ]
+++

Un [WAF](https://fr.wikipedia.org/wiki/Web_application_firewall) exa­mine chaque requête HTTP pour protéger les applications web face à différents vecteurs d'attaques pour minimiser les infections. It can auto­ri­ser to tran­si­ter until the app­pli­tion, or block them, aler­ter, consi­gner if they are judged awkward.

{{< fig "waf.en.png" "HTTP request path facing a WAF" >}}

alwaysdata uses the WAF ModSecurity and the free set [OWASP Modsecurity Core Rule Set](https://coreruleset.org/) (CRS).

## Browse web application firewall

{{< fig "admin-panel_add-site-waf.en.png" "" >}}

### Available Profiles

| Profile   | Description                                                                                                                      |
| --------- | -------------------------------------------------------------------------------------------------------------------------------- |
| None      | (default)                                                                                                     |
| Basic     | HTTP strict adherence                                                                                                            |
|           | Ambient robot detection                                                                                                          |
| Strong    | Basic Profiling Set                                                                                                              |
|           | Detection of execution code at dis­tance (RCE)                                                                |
|           | Attack detection type [Cross-Site Scripting (XSS)](https://fr.wikipedia.org/wiki/Cross-site_scripting)        |
|           | Detecting [SQL injection](https://fr.wikipedia.org/wiki/Injection_SQL)                                                           |
| Full      | The Strong Profil's Entire                                                                                                       |
|           | Detecting relaxed attacks at PHP launching                                                                                       |
|           | Attacking detection by local file inclusion (LFI)                                                             |
|           | Attack detection by [Including Disconnecting File (RFI)](https://fr.wikipedia.org/wiki/Remote_File_Inclusion) |
| WordPress | Complete Profiles                                                                                                                |
|           | WordPress Special Gles                                                                                                           |
| Drupal    | Complete Profiles                                                                                                                |
|           | Specific awards in Drupal                                                                                                        |
| Nextcloud | Complete Profiles                                                                                                                |
|           | Specific issues in Nextcloud                                                                                                     |
| Dokuwiki  | Complete Profiles                                                                                                                |
|           | Specific awards at Dokuwiki                                                                                                      |

{{% notice note %}}
The action of a pro­tec­ment will be driven by an increase in latency during the processing of an HTTP request. This latency, in the order of a few mil­li­se­condes, augments with the degree of pro­tec­tion.
{{%/notice %}}

### Exclude from Records

Depending on your use case, the **behavior of the WAF may be too restrictive**. It is also possible that it generates **false positives** when parsed. If you feel that its behavior is not appropriate, you have the possibility to exclude some of the reactions used in the analysis.

Only the **exclude** number must be specified. You can find it in the Sites logs (`$HOME/admin/logs/sites`). Example:

```
[08/Jan/2019:11:09:19 +0100] [waf] - <IP attaquante> "GET /?param=%22><script>alert(1);</script> HTTP/1. " - 941100 | XSS Attack Detected via libinjection' with value: "><script>alert(1);</script>
[08/Jan/2019:11:09:19 +0100] [waf] - <IP attaquante> "GET /? aram=%22><script>alert(1);</script> HTTP/1. " - 941110 | XSS Filter - Category 1: Script Tag Vector' with value: <script>
[08/Jan/2019:11:09:19 +0100] [waf] - <IP attaquante> "GET /? aram=%22><script>alert(1);</script> HTTP/1. " - 941160 | NoScript XSS InjectionChecker: HTML Injection' with value: <script>
```

So it would be `941100`, `941110` and `941160` that might be indicated.

{{% notice warning %}}
Please make sure to gradually add new ones as the exclusion is applicable throughout the site. Indeed, even if adding a large number of exclusions may improve navigation in some cases protection will then be diminished in all other cases.
{{%/notice %}}

### Exclude from paths

This type of exclusion allows you to **avoid parsing pages started by the specified path**. By entering `/foo/` for example, `www.my-site.com/foo/` will be excluded from parsing just like query strings: `www.my-site.com/foo/?param=bar`. To also exclude `www.my-site.com/foo/bar` and `www.my-site.com/foo/script.php`, add a _wildcard_ : `/foo/*`. Finally, if you want to substitute any character (especially that would change regularly), `?` can be used.

So, to drop the parse `www.my-site.com/foo/barBaz/`, `foo` and `Baz` having any _strings_ parses, the excluding path would be: `/*/bar?/`.

{{% notice tip %}}
Let’s take the case of a WordPress site that has similar logs to previous ones. If these issues are triggered when navigating through the admin interface of the blog, then it is possible to exclude them permanently.
However, the blog itself will no longer be protected from these attack attempts. In this case, it is better to exclude the path (example: /wp-admin/\*) so that all your actions on the administration interface are no longer affected by WAF's analysis.
{{%/notice %}}

_[query strings](https://en.wikipedia.org/wiki/Query_string)_ cannot be used in these exclusions.

### Exclude from IP

It may be integering to exclude **extra IPs** (specific IP or IP ranges) to avoid blocked tools or people.

Let's take the example of [WPScan](https://wpscan.com/): by activating it on a WordPress site some of the requests it makes may be blocked. Excluding files or paths would not be effective as it observes many URLs. The solution is to exclude the HTTP server on which WPScan is installed so that it can function normally.

> The Noun Project

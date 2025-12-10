+++
url = "/sites/"
title = "Websites"
pre = "<i class='fas fa-fw fa-globe'></i> "
archetype = "chapter"
weight = 10
tags = [ "http", "site" ]
+++

For an address hosted by alwaysdata to be accessible over HTTP/HTTPS it **must** displayed in **Web > Sites**. Choose the [langage](languages) or type of your choice and adjust them.

You can have as many sites as you want on a single account. Note that this entails a risk of security, as the isolation is at the level of the accounts.

An excerpt of the logs is shown in the alwaysdata admin interface (**Logs** - 📄) and the processes in progress in the **Advanced> Process > Web** menu.

{{% notice note %}}
If your script needs to authorize certain IPs, allow these [IP address ranges](security/ip-ranges).
{{%/notice %}}

## Resources

- [API](https://api.alwaysdata.com/v1/site/doc/)
- [Create a site](add-a-site)
- [External HTTP addresses](use-external-addresses) (non-DNS domains)

* [User Program](user-program)
* [Address Redirect](redirect)
* [Custom Apache](apache-custom)
* [Static files](static-files)

- [HTTP Stack](http-stack)
- [Apache Configuration](configure-apache)
- [.htaccess file](htaccess-file)

* [Restart a site](restart-a-site)
* [Change provider](./transfer-in)
* [Change website address](sites/change-a-website-address)
* [Move a site](move-a-site)
* [Unactivate a site](deactivate-a-site)

- [Catch-all](./catch-all)
- [Equal obligations on the Internet](legal-requirements-on-internet)

* [Uninfect a site](clean-up-a-site)
* [Restore Site](backups/restore-a-site)
* [Connection to upstream](connection-to-upstream)
* [Freight issues](./troubleshooting)
* [Various questions](./misc)

## Protection of Internet communications

- [Redirect HTTP to HTTPS](security/ssl-tls/redirect-http-to-https)
- [TLS] (security/ssl-tls/configure-tls)
- [Add SSL Certificate](security/ssl-tls/add-a-ssl-certificate)
- [Let's Encrypt Certificates](security/ssl-tls/lets-encrypt)

## Customization

- [Customize error pages](custom-error-pages)
- [Parse processes](analyze-processes)
- [Web Performance](web-performances)
- [Hearing Peak](anticipate-peak-audience)
- [Format HTTP logs](formatting-http-logs)

* [HTTP cache](sites/http-cache)
* [Enable HTTP Cache on WordPress](sites/activate-http-cache-on-wordpress)

- [WAF](sites/waf)

* [Monitoring probes](use-probes)

## External links

- Availability of a site: [Where's It Up?](https://wheresitup.com/), [Screenshot Guru](https://screenshot.guru/) (with screenshot)
- Know the DNS resolution of an address: [DNSwatch](https://www.dnswatch.info/)

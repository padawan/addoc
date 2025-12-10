+++
url = "/securite/bug-bounty"
title = "Bounty Bug"
layout = "man"
hidden = true
tags = [ "" ]
+++

> **[Bug Tracking Interface](https://security.alwaysdata.com/)**

## GEOM_REGISTERS

We believe that no technology is perfect and that working with competent security researchers is crucial to identifying the weaknesses of our technology. If you think you found a security bug in our service, we are happy to work with you to resolve the problem quickly and ensure that your discovery is properly rewarded.

Let us know as soon as possible after a potential security problem has been discovered, and we will do everything we can to resolve the problem quickly. Give us a reasonable time to resolve the problem before any disclosure to the public or to a third party.

Test vulnerabilities only on accounts you own or accounts for which you have authorization from the account holder to perform testing.

Never use a discovery to compromise/exfilter data or rotate to other systems. Use proof of concept only to show a problem.

Whether sensitive information — such as personal information, identifiers, etc. — are accessible as part of a vulnerability, they must not be saved, stored, transmitted, or otherwise consulted after the initial discovery. All sensitive information must be returned to _alwaysdata_ and no copy of this information must be stored.

**Any type of denial of service attack (DDoS) is strictly prohibited, as well as any interference with the network equipment and infrastructure of _alwaysdata_.**

Do not attempt to exploit the bug and access internal data for other vulnerabilities. We will determine the gravity and reward accordingly.

If you find the same vulnerability several times, please create a single report and possibly use comments. You will be awarded according to your findings.

**Violation of one of these fees may result in ineligibility for a premium and/or withdrawal from the program.**

### Legal Considies

We will not initiate civil action or lodge complaints from the law enforcement agencies for accidental and bona fide violations of this policy. We will follow the activities conducted against you for bypassing the technological measures we have used to protect applications within the framework of this program.

If a third party action is brought against you and you have complied with this security policy, we will take steps to inform you that your actions have been conducted in accordance with this policy.

It is also important to note that we will not take legal action against you simply because we have provided evidence of the security fault concept. Please follow the instructions listed in the [Proof of Concept](#preuves-de-concept) section below to ensure that your proof of concept is sufficiently detailed to demonstrate the problem and still follows the above guidelines.

## Period and tests

The search term includes only the following addresses:

```txt
- https://www.alwaysdata.com
- https://admin.alwaysdata.com
- https://webmail.alwaysdata.com
- https://api.alwaysdata. om
- ssh://ssh-[accountid].alwaysdata.net
- https://webdav-[accountid].alwaysdata.net
- ftp://ftp-[accountid].alwaysdata.net
```

Vulnerabilities reported on other services or applications will not be considered.

Once processed, reports are _public_. Any private information can be transmitted via a support ticket on [our admin interface](https://admin.alwaysdata.com/).

When testing a bug, please keep in mind:

- Use test accounts to avoid unintentionally compromising the confidentiality of our users;
- When trying to show root permissions with the following primitives in a Vulnerable process, please use the following commands:
  - Read: `cat /proc/1/maps`
  - Write: `touch /root/<accountid>`
  - Execute: `id, hostname, pwd`

**Minimize chaos.** Respect the program at all times. Do not use automated scanners/tools — these tools include useful loads that could trigger status changes or damage production systems and/or data.

**Before causing damage or potential damage: stop, report what you found and request additional test permission.**

The vulnerability reports are reviewed by our security analysts. Reports must be submitted using our **[bug tracking interface](https://security.alwaysdata.com/)**.

_All reports sent by email or our support interface will be rejected._

Our analysis is always based on exploiting the worst of the vulnerability cases, just as the compensation we pay.

We are continually working on our bounty bug program. We aim to respond to incoming submissions as quickly as possible and do our utmost to ensure that bugs are fixed within 10 days of sorting. Rewards will be paid when the patch is applied.

## Rewards

We offer premium rewards.

The following is simply a reward indicator, but does not reflect what the final decision might be. _We value quality reports and proof of concept._

| Qualification | Examples of vulnerabilities (non-exhaustive list)                                                    | CVSS Score                                 | Bounty      |
| ------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------ | ----------- |
| None          |                                                                                                                         | N/A                                        | No Bounty   |
| Low           | Access restricted parts of third-party elements or their plugins (blog, forum, etc.) | 0.1 - 3.9  | Up to €50   |
| Average       | Grant user account permissions/configurations without access to their content                                           | 4.0 - 6.9  | Up to 200 € |
| Highest       | Access customer data/information                                                                                        | 7.0 - 8.9  | Up to €350  |
| Critical      | Access in read/read-write mode to the central platform architecture                                                     | 9.0 - 10.0 | Up to €500  |

### Eligible

We are pleased to thank all those who submit valid reports that help us improve the security of _alwaysdata_. However, only those who meet the following eligibility requirements can receive a monetary reward:

- You must be the first to report a flaw;
- The fault must be qualified;
- Any vulnerabilities found must be reported no later than 24 hours after its discovery and exclusively via our support interface;
- You must send a clear text description of the report as well as steps to reproduce the problem using standard Linux tools. We may ask you to send proof of concept that reproduces the flaw (e.g. a shell script);
- You must avoid tests that could cause our service to degrade/interrupt (refrain from using automated tools and limit requests per second);
- You must not disclose, manipulate or destroy user data;
- You must not be a former employee (since 1 year) or a current employee of _alwaysdata_, or any of his or her subcontractors.

No disclosure of vulnerabilities, including partial disclosure, is permitted before the patch is applied and we accept the release.

## Proof of concept

- XSS: For XSS, a simple `alert(document.domain)` should suffice;
- RCE: Please execute harmless code only. Please refer to section [Test](#périmètre-et-tests);
- SQLi: Report this as you have an SQL error indicating an SQL injection or are able to disclose the SQL server version number;
- Invalid redirect: Set the redirect endpoint to `http://example.org` _if possible_;
- CSRF: Attach a file to show the problem or paste the code into a code block in your report;
- SSRF: Do not play on internal networks. Report as soon as you think you have a potential SSRF issue and we will review it for you;
- LFI: The same is true here — please do not go against the guidelines listed in the [Program Reggles] section (#règles). We will report on LFI reports in a development environment to ensure they are validated.

## Qualified Scrap

- SQL Injection;
- Find an undesirable numeric user ID (even yours) in views, which allows you to forge requests;
- Exposure of sensitive member information[^1] ;
- Exposure of internal tools;
- Exposure of configuration files or secrets;
- Repertory Path Problems;
- Local file access and manipulation (LFI, RFI, XXE, SSRF, XSPA);
- Local File Disclosure (LFD);
- Code injections (HTML, JS, SQL, PHP, ...) ;
- Cross-Site Scripting (XSS);
- Cross-site Request Falsification (CSRF) with a strong impact on the security;
- Server request spoofing (SSRF);
- Open redirect;
- Remote code execution (RCE);
- Authentication & Session Management
- Direct object references not secured;
- CORS with a strong impact on the security;
- Missing "secured" flags on authentication cookies;
- Access control problems;
- Horizontal and vertical privilege elevation.

## Invalid reports

The following list includes vulnerability reports not accepted by our services:

- Any hypothetical flaws or best practices without exploitable POCs;
- Connection, disconnect, unauthenticated or low value;
- Absence of connected HTTP headers to the security that do not directly cause a flaw;
- Prevention/absence of SPF/DMARC records;
- Reports on unsecured SSL/TLS encryption (unless you have a working POC);
- Brute force attacks/password reuse;
- User Numbers Attacks;
- Premium Phone Number Attacks;
- Disclosure of known public files or directories (e.g. robots.txt);
- Massive automated actions on the platform via robots/crawling (unless this collects sensitive information about members);
- XSS Self;
- No cookies flags;
- Best Practices SSL/TLS;
- Mixed Content Warnings;
- Attacks by denial of service;
- XSS on "HTTP Host Header" ;
- Click/UI Stop;
- Disclosure Software Version;
- Stack tracks or path disclosure;
- Physical or social ingenious attempts;
- Recently Disclosed Scraps (same day);
- Presence of autocomplete attribute on web forms;
- Sizes affecting browsers or obsolete platforms;
- Problems requiring physical access to the victim's computer/device/interface (e.g. if the victim left the victim open or the attacker was the victim);
- Disconnection and other instances of low gravity CSRF;
- Reports from automatic web vulnerability scanners (Acunetix, Vega, etc. ) that have not been validated;
- Reports concerning third party applications that we provide to our customers but which are not directly part of our system (phpMyAdmin, Roundcube Webmail, etc. , if the vulnerability does not directly expose client data and/or metrics;
- Reports on third party applications that we provide to our customers but which are not directly part of our system (phpMyAdmin, Webmail Roundcube, etc. , unless the vulnerability exposing user data and/or metrics has been fixed for more than a month in the published version and we are not up to date;
- Reports about known vulnerabilities in subcomponents (e.g. OpenSSH) that have just been disclosed. We aim to apply security patches in 30 days or less so recently disclosed vulnerability reports are not relevant;
- Reports about sites or applications hosted by our customer. unless the vulnerability is due to our platform in conjunction with the client application;
- Reports of vulnerabilities from third party applications that we use that are either unknown, uncorrected, or fixed in unpublished versions.

Note that:

- account names are [accessible in many ways](remote-access/misc#lister-les-comptes);
- addresses in `.alwaysdata.net` are linked to our customers' accounts. Their flaws do not fall within our competence;
  - including if they disclose their login information;
- The `/tmp` directory is a [shared directory](remote-access/misc#répertoire-tmp);
- `https://files.alwaysdata.com` and `https://share.alwaysdata.com` represent public files;
- password reset link expires after 3 days or next login at the admin interface;
- a user can re-use an old password. This is not a [good practice listed by NIST](https://pages.nist.gov/800-63-3/sp800-63-3.html);
- email verification (whether registered or changed profile information) is only a practice, not a flaw;
- HTML and XSS injections in the administration interface would only target the attacker and therefore cannot be vulnerabilities;
- we do not use CDN and our IPs are public;
- the version number of the software we use [cannot be terminating](security/security-upgrades).

[^1]: name, phone number, email, physical address, physical identity card

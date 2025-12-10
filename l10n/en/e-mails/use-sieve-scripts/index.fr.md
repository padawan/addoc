+++
url = "/emails/user-les-scripts-sieve/"
title = "How to use Sieve scripts"
layout = "howto"
hidden = true
tags = [ "email" ]
+++

[Sieve](http://sieve.info/) is a language for filtering emails. It is used to add complex tricks, which could not be added via the [filtering filters](e-mails/add-a-filter-rule).

{{< fig "images/admin-panel_mailbox_sieve.png" "Admin interface: Emails - Sieve Script" >}}

The final script is stored in your account's `$HOME/admin/mail/[domaine]/[boite]/filter_user.sieve` file. You can read it to help debug your script, but not edit it.

## Supported extensions

| Extension                                                                   | Description                                                                                                 |
| --------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| body                                                                        | Check the presence of one or more chains of characters in the body of an email                              |
| comparator-i;ascii-numeric                                                  | Extract numbers from the text and compare them to see if this matches                                       |
| copy                                                                        | Specifies that a copy must be used to perform the action                                                    |
| date                                                                        | Perform actions based on sending/receiving an email date/time                                               |
| duplicate                                                                   | Detect if duplicated                                                                                        |
| editer                                                                      | Adds or removes text to headers                                                                             |
| character encoding                                                          | Enables the numeric encoding of special characters                                                          |
| enotify                                                                     | Send notifications                                                                                          |
| envelope                                                                    | Evaluates the envelope ("from", "to"...) |
| environment                                                                 | Test different execution environment values                                                                 |
| fileinto                                                                    | Delivers the email in the specific folder                                                                   |
| drilling part                                                               | Allows orders executed in all MIME parts of the email                                                       |
| [currency symbol] ihave | Test if a Sieve extension is available and, if so, perform its action                                       |
| imap4flags                                                                  | Adds IMAP indicators and keywords to messages                                                               |
| include                                                                     | Allows to include a Sieve script in another                                                                 |
| index                                                                       | Allows to match specific header fields by index                                                             |
| mailbox                                                                     | Check if a specific directory exists                                                                        |
| mime                                                                        | Test specific MIME parts of the message                                                                     |
| extracttext                                                                 | Extract text from MIME parts                                                                                |
| regex                                                                       | Use regular expressions                                                                                     |
| discard                                                                     | Decline message delivery                                                                                    |
| Relational                                                                  | Allows relational comparisons                                                                               |
| subaddress                                                                  | Test boundary elements of the local part of addresses                                                       |
| vacation                                                                    | Automatic Responses                                                                                         |
| variables                                                                   | Allows to add variables                                                                                     |

## Examples

### Add a `<SPAM>` prefix to a mail containing a keyword to be defined (either in its subject or body of text)

```
require ["editheader", "variables", "body"];
if allof (
header :contains "subject" "word",
header :matches "Subject" "*"
)
{
deleteheader "Subject";
addheader "Subject"<SPAM> ${1}";
}
elsif allof (
body :content "text" :contains "word",
header :matches "Subject" "*"
)
{
deleteheader "Subject";
addheader "Subject"<SPAM> ${1}";
}
```

### Extract message headings into automatic replies

```
require ["variables", "vacation"];

# Storing the subject in variable
if header :matches "Subject" "*" {
        set "subj" "**${1}**";
}

# Auto Responder
vacation
  :days 1
  :subject "Absence [Was: ${subj}]"
"Hello,
we have received your message correctly:

${subj}

We are currently away and will respond to it upon our return.";
```

---

## Links

- [RFC 5228](https://tools.ietf.org/html/rfc5228)

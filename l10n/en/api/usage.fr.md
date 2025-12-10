+++
url = "/api/usage/"
title = "API Usage"
weight = 5
tags = [ "api" ]
+++

## Identification

```sh
$ curl --basic --user APIKEY: https://api.alwaysdata.com/v1/account/
```

Your tokens are available in the **[Profil]menu (accounts/tokens)**.

{{% notice warning %}}
For the use of your tokens, remember the two points (:) after the key, This allows you to specify that the password is not necessary.
{{%/notice %}}

{{% notice info %}}
A limit of the number of requests to the API applies. More information [ici](#rate-limit).
{{%/notice %}}

### Related resources

If you access resources linked to a specific user or account, you need to specify it when authenticating using one of the following parameters:

- **account**: this is the account you want to access. If for example
  you have multiple accounts but want to access a specific account resource.
- **customer**: if you have some permissions on another user,
  then you need to specify their email address.

For example, access FTP users in your _mycompany_ account in this way:

```sh
$ curl --basic --user "APIKEY account=mycompany:" https://api.alwaysdata.com/v1/ftp/
```

## Format

The managed formats are as follows:

- [JSON](https://www.json.org/) (default)
- [XML](https://fr.wikipedia.org/wiki/Extensible_Markup_Language)
- [HTML](https://fr.wikipedia.org/wiki/Hypertext_Markup_Language) (for answer only)

It can be specified in the URI:

```sh
$ curl --basic --user APIKEY: https://api.alwaysdata.com/v1/account/?_format=xml
```

Or via HTTP header:

```sh
$ curl --basic --user APIKEY: --header 'Accept: application/xml' https://api.alwaysdata.com/v1/account/
```

## HTTP Headers

| HTTP address           | Description                  | Default value |
| ---------------------- | ---------------------------- | ------------- |
| alwaysdata-synchronous | Query execution in sync mode | no            |

## Rate-limit

A limit of actions per minute is set up:

- 10 requests per minute
- 50 requests for permanent connections
- 250 requests for _safe_ methods like `GET`

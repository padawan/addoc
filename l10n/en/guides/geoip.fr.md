+++
url = "/guides/geoip/"
title = "How to block visits via GeoIP"
layout = "howto"
hidden = true
tags = [ "security", "site" ]
+++

[MaxMind DB](https://www.maxmind.com/en/geoip2-services-and-databases)[^1] is a GeoIP module [Apache](sites/configure-apache) that aims to locate a user based on their IP address.

## Setup

Run the following commands in [SSH](remote-access/ssh) at the root of the account:

{{% notice note %}}
Take the [latest available version of `mod_maxminddb`](https://github.com/maxmind/mod_maxminddb)
{{% /notice %}}

```sh
mkdir mod_maxminddb
cd mod_maxminddb/
wget https://github.com/maxmind/mod_maxminddb/releases/download/1.2.0/mod_maxminddb-1.2.0.tar.gz
tar xf mod_maxminddb-1.2.0.tar. z 
cd mod_maxminddb-1.2.0/
./configure --with-apxs=/usr/alwaysdata/apache/latest/bin/apxs && make
cp ./src/.libs/mod_maxminddb.so ~/
cd
rm -en mod_maxminddb
```

Then add in the **Web > Configuration** menu of your alwaysdata admin interface:

```
maxminddb_module $HOME/mod_maxminddb.so
```

Finally create an account on their interface to receive one of their database: [gratuite](https://dev.maxmind.com/geoip/geolite2-free-geolocation-data?lang=en) or [payante](https://www.maxmind.com/en/geoip2-databases) as required.

## Uses

### Block some countries

In this example we use the free basis that we put at the root of the account and we block China and the United States.

Add at the top of a `.htaccess` to the root of the site:

```
MaxMindDBEnable On
MaxMindDBFile COUNTRY_DB $HOME/GeoLite2-Country.mmdb
MaxMindDBEnv COUNTRY_CODE COUNTRY_DB/country/iso_code

SetEnvIf COUNTRY_CODE CN BlockCountry
SetEnvIf COUNTRY_CODE US BlockCountry

Deny from env=BlockCountry
```

### Allow only some countries

In this example we use the free basis that we put at the root of the account and only allow France.

Add at the top of a `.htaccess` to the root of the site:

```
MaxMindDBEnable On
MaxMindDBDBFile COUNTRY_DB $HOME/GeoLite2-Country.mmdb
MaxMindDBEnv COUNTRY_CODE COUNTRY_DB/country/iso_code

SetEnvIf COUNTRY_CODE EN AllowCountry

Deny from all
Allow from env=AllowCountry
```

[^1]: MaxMind DB can also be used for geographic marketing and provides city bases.

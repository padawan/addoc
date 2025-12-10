+++
url = "/sites/anticiper-un-pic-daudience/"
title = "How to anticipate peak audience"
layout = "howto"
hidden = true
tags = [ "http", "site" ]
+++

You are planning a TV / radio passage that may lead to more visits and do not know that your site supports the load? Here are shares that can be taken upstream:

- **isolate the site** by account - so as not to manage other sites, resources being shared at the account level;
- enable **[HTTP cache](sites/http-cache)** on your administration interface and/or application level using Memcached, Redis [^1] or any other software cache;
- switch to the most recent language versions possible - to improve performance;
- redirect to a **[static page](sites/static-files)** - using far fewer resources, they are faster to return.

To observe the behavior of your application you can also perform a **load test** (with `ab` for example).

## Example with `ab`

We want to know if our commercial site can manage 300,000 visits a day.

_The following test makes 100 requests on the home page at a time of 10 (in parallel)._

```sh
$ ab -c 10 -n 100 https://www.alwaysdata.com/en/
This is ApacheBench, Version 2. <$Revision: $1843412 >
Copyright 1996 Adam Twiss, Zeus Technology Ltd, http://www.zeustech.net/
Licensed to The Apache Software Foundation, http://www. pache.org/

Benchmarking www.alwaysdata.com (be patient)..... one


Server Software: nginx
Server Hostname: www. lwaysdata. om
Server Port: 443
SSL/TLS Protocol: TLSv1. ,ECDHE-RSA-AES128-GCM-SHA256,2048, 28
Server Temp Key: X25519 253 bits
TLS Server Name: www. lwaysdata. om

Document Path: /en/
Document Length: 77003 bytes

Concurrency Level: 10
Time taken for tests: 7. 38 seconds
Complete requests: 100
Failed requests: 52
   (Connect: 0, Receive: 0, Length: 52, Exceptions: 0)
Non-2xx managers: 52
Total transferred: 3938476 bytes
HTML transferred: 3893588 bytes
Requests per second: 13. 7 [#/sec] (mean)
Time per request: 753. 54 [ms] (mean)
Time per request: 75. 75 [ms] (mean, across all competitor requests)
Transfer rate: 510. 7 [Kbytes/sec] received

Connection Times (ms)
              min mean[+/-sd] median max
Connect: 83 112 100. 101 1099
Processing: 36 576 942. 227 5045
Waiting: 36 503 933. 99 5044
Total: 121 688 952. 329,5179

Percentage of the requests served within a certain time (ms)
  50% 329
  66% 464
  75% 822
  80% 870
  90% 2131
  95% 2648
  98% 4845
  99% 5179
 100% 5179 (longest request)
```

The important information is: `Requests per second: 13.27 [#/sec] (mean)`.

300,000 visits in 10 hours (small day) corresponds to 8.3 requests per second. The current configuration is therefore compatible.

- [`ab`](https://httpd.apache.org/docs/2.4/programs/ab.html)

## Links

- 2 external load testing services:
  - [Loader.io](https://loader.io/)
  - [K6](https://k6.io/)

[^1]: Both software are available on [Cloud Privacy](accounts/billing/private-cloud-prices).

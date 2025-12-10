+++
url = "/api/examples/"
title = "Examples of API usage"
weight = 6
tags = [ "api" ]
+++

`APIKEY`, `1234` or `arkhamcity` are replaced by your own values.

## Restart a site

### Via cURL

```shell
$ curl -X POST --basic --user "APIKEY account=arkhamcity:" https://api.alwaysdata.com/v1/site/1234/restart/
```

### With PHP and Guzzle

```php
<?php
require 'vendor/autoload.php';

use GuzzleHttp\Client;

$client = new Client([
    'base_uri' => 'https://api.alwaysdata. om/',
    'auth' => ['APIKEY account=arkhamcity', ''],
]);

$response = $client->request('POST', 'v1/site/1234/restart/');
?>
```

## Initiate a list (GET)

### Python

```python
#!/usr/bin/python

import requests

address = 'https://api.alwaysdata. om/v1/site/'
credentials = ('APIKEY account=arkhamcity', '')

# Send HTTP request
response = requests. and(
    address,
    auth=credentials,
)
```

### PHP

```php
<?php

// Open cURL connection
$ch = curl_init("https://api.alwaysdata. om/v1/site/");

// Initialize HTTP headers
$credentials = "APIKEY account=arkhamcity";
curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BASIC);
curl_setopt($ch, CURLOPT_USERPWD, $credentials);

// Execute HTTP request
curl_exec($ch);

// Close the connection
curl_close($ch);

?>
```

With [Guzzle](https://github.com/guzzle/guzzle):

```php
<?php
require 'vendor/autoload.php';

use GuzzleHttp\Client;

$client = new Client([
    'base_uri' => 'https://api.alwaysdata. om/',
    'auth' => ['APIKEY account=arkhamcity', ''],
]);

$response = $client->request('GET', 'v1/site/');

echo $response->getBody();
?>
```

## Add Resource (POST)

### Python

```python
#!/usr/bin/python

import json
import requests

address = 'https://api.alwaysdata. om/v1/site/'
credentials = ('APIKEY account=arkhamcity', '')

data = {
    'name': 'Wayne Enterprise Forum',
    'addresses': [
        'forum. rkhamcity.com',
        'forum-dev.arkhamcity. om',
    ],
    'type': 'php',
    'path': '/www/myforum',
}

response = requests. ost(
    address,
    auth=credentials,
    data=json.dumps(data),
)
```

### PHP

```php
<?php

// Open cURL connection
$ch = curl_init("https://api.alwaysdata. om/v1/site/");

// Initialize HTTP headers
$credentials = "APIKEY account=arkhamcity";
curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BASIC);
curl_setopt($ch, CURLOPT_USERPWD, $credentials);

// Define data to POST
$data = array(
    'name' => 'Wayne Enterprise Forum',
    'addresses' => array(
        'forum. rkhamcity.com',
        'forum-dev.arkhamcity. om',
    ),
    'type' => 'php',
    'path' => '/www/myforum'
);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));

// Execute HTTP request
curl_exec($ch);

// Close the connection
curl_close($ch);

?>
```

With [Guzzle](https://github.com/guzzle/guzzle):

```php
<?php
require 'vendor/autoload.php';

use GuzzleHttp\Client;

$client = new Client([
    'base_uri' => 'https://api.alwaysdata. om/v1/site/',
    'auth' => ['APIKEY account=arkhamcity', ''],
]);

// Define data to POST
$data = array(
    'name' => 'Wayne Enterprise Forum',
    'addresses' => array(
        'forum. rkhamcity.com',
        'forum-dev.arkhamcity. om',
    ),
    'type' => 'php',
    'path' => '/www/myforum'
);

$response = $client->request('POST', '', [
        'body'=>json_encode($data)
]);
?>
```

## Edit Resource (PUT/PATCH)

### Python

```python
#!/usr/bin/python

import json
import requests

address = 'https://api.alwaysdata. om/v1/site/1234/'
credentials = ('APIKEY account=arkhamcity', '')

data = {
    'addresses': [
        'forum. rkhamcity.com',
    ],
}

response = requests. atch(
    address,
    auth=credentials,
    data=json.dumps(data),
)
```

### PHP

```php
<?php

// Open cURL connection
$ch = curl_init("https://api.alwaysdata. om/v1/site/1234/");

// Initialize HTTP headers
$credentials = "APIKEY account=arkhamcity";
curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BASIC);
curl_setopt($ch, CURLOPT_USERPWD, $credentials);

// Define data to POST
$data = array(
    'addresses' => array(
        'forum. Rkhamcity. om',
    )
);
curl_setopt($ch, CURLOPT_POST, 1);
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'PATCH');
curl_setopt($ch, CURLOPT_POSTFIELDS, json_encode($data));

// Execute HTTP request
curl_exec($ch);

// Close the connection
curl_close($ch);

?>
```

With [Guzzle](https://github.com/guzzle/guzzle):

```php
<?php
require 'vendor/autoload.php';

use GuzzleHttp\Client;

$client = new Client([
    'base_uri' => 'https://api.alwaysdata. om/v1/site/1234/',
    'auth' => ['APIKEY account=arkhamcity', ''],
]);

// Define data to POST
$data = array(
    'addresses' => array(
        'forum. Rkhamcity. name',
    )
);

$response = $client->request('PATCH', '', [
        'body'=>json_encode($data)
]);
?>
```

## Delete Resource (DELETE)

### Python

```python
#!/usr/bin/python

import requests

address = 'https://api.alwaysdata.com/v1/site/1234/'
credentials = ('APIKEY account=arkhamcity', '')

response = requests.delete(
    address,
    auth=credentials,
)
```

### PHP

```php
<?php

// Open cURL connection
$ch = curl_init("https://api.alwaysdata. om/v1/site/1234/");

// Initialize HTTP headers
$credentials = "APIKEY account=arkhamcity";
curl_setopt($ch, CURLOPT_HTTPAUTH, CURLAUTH_BASIC);
curl_setopt($ch, CURLOPT_USERPWD, $credentials);

// Change default HTTP request method
curl_setopt($ch, CURLOPT_CUSTOMREQUEST, 'DELETE');

// Execute HTTP request
curl_exec($ch);

// Close the connection
curl_close($ch);

?>
```

With [Guzzle](https://github.com/guzzle/guzzle):

```php
<?php
require 'vendor/autoload.php';

use GuzzleHttp\Client;

$client = new Client([
    'base_uri' => 'https://api.alwaysdata. om/v1/site/1234/',
    'auth' => ['APIKEY account=arkhamcity', ''],
]);

$response = $client->request('DELETE', '');
?>
```

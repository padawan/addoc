+++
url = "/en/donor-bases/rabbitmq/plugin-de-management"
title = "RabbitMQ Management Plugin"
layout = "man"
hidden = true
tags = [ "database", "rabbitmq" ]
+++

RabbitMQ's [management plugin](https://www.rabbitmq.com/management.html) can be used on [Cloud Privacy](accounts/billing/private-cloud-prices). Only [access management](https://www.rabbitmq.com/management.html#permissions) will be available.

## Setting up

Create a [Reverse proxy](sites/add-a-site#configuration) site pointing to `https://localhost:15672`. Add to its vhost directives:

```txt
SSLProxyCheckPeerCN off
SSLProxyCheckPeerName off
```

You can log in with any of your RabbitMQ users.

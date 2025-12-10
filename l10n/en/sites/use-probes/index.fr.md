+++
url = "/sites/utiliser-les-sondes-de-monitoring/"
title = "How to use monitoring probes"
layout = "howto"
hidden = true
tags = [ "http", "site" ]
+++

For our users who have a dedicated / Gold server, it is possible to program monitoring probes in order to verify that a website is working properly. If a problem is detected by a probe, an alert is sent to our team.

## Setup

The configuration of a probe allows to configure different options:

- address: the exact address that will be monitored by the probe, possibly via HTTP authentication;
- notification: when to start an alert and how to contact the app manager;
- answer: checking the HTTP response content with a text (default probe checks that the HTTP response is of type 2xx).

## Responsibility

The interventions initiated by the probes are invoiced if the responsibility for the application is committed.

Examples (non-exhaustive list):

- any problems that result from the user's incorrect use of the server;
- abnormal behavior of user apps;
- any performance issues not related to server or network malfunctioning;
- saturation of server resources by user apps;
- any network malfunction whose origin would not be the responsibility of alwaysdata.

{{% notice note %}}
A probe is invoiced at €10 (tax excl.) per month and each intervention triggered by a failure not having our responsibility is invoiced at €100 (tax excl.)
{{%/notice %}}

+++
url = "/avance/docker"
title = "Docker"
layout = "man"
hidden = true
tags = [ "" ]
+++

{{% notice note %}}
[Docker](https://www.docker.com/) is available only on [Private Cloud] environments (accounts/billing/private-cloud-prices).
{{%/notice %}}

Docker is running in [rootless]mode (https://docs.docker.com/engine/security/rootless/).

## Setup

After [contacted support](https://admin.alwaysdata.com/support/add) to install Docker on the server, it takes **for each account** to use it:

- execute [SSH](remote-access/ssh):

```sh
$ dockerd-rootless-setuptool.sh install
```

This must return:

```sh
[INFO] dockerd-rootless.sh needs to be started (e.g. by creating a service):
dockerd-rootless.sh 

[INFO] Creating CLI context "rootless"
Successfully created context "rootless"
```

- create [service](services):
  - _Command_: `dockerd-rootless.sh`

> The installation is finished, you can use the `docker` command normally.

## Usage

You can use Docker to spin [sites](sites), [services](services), of [scheduled tasks](tasks) or simply [SSH](remote-access/ssh).

To run a site with Docker, you will need to use the [user program](sites/user-program) type and enter your `docker run` command. It will require your Docker container to listen in HTTP on port `$PORT`, for example:

```txt
docker run -p $PORT:80 gitlab/gitlab-ee:latest
docker run -p $PORT:8080 jenkins/jenkins:lts-jdk11
```

You will need to consult your Docker image documentation to find out what exactly to say.

By default, Docker listen on the private IP addresses of the account. If it is necessary for it to be directly reachable from outside, it is necessary to [specify the external IP](https://docs.docker.com/engine/containers/run/#exposed-ports) with the `-p` option.

{{% notice warning %}}
**Docker containers are also under the responsibility of our users. No information or support can be provided by alwaysdata.** In particular, Docker images are managed by software such as Apache, PHP, MySQL, Redis... which will not be administed, configured, or monitored by alwaysdata, as opposed to applications that would run without Docker. For this reason, we strongly invite our users to use Docker only if needed, and **systemically** ask for advice from our support before using a Docker image. In many cases, it will be preferable to do without Docker - for example, using our [marketplace](marketplace) or a [installation guide](guides), allowing to test alwaysdata info, better performance and increased reliability.
{{%/notice %}}


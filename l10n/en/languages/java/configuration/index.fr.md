+++
url = "/en/languages/java/configuration/"
title = "Configure Java"
hidden = true
layout = "man"
tags = [ "java" ]
+++

## Supported Versions

|    |
| -- |
| 25 |
| 21 |
| 17 |
| 11 |
| 8  |

The default version is editable in the alwaysdata administration, **Java Environment > Administration**. This version is especially used when you start `java`.

Versions are not forcefully [already installed](languages#-versions).

{{% notice note %}}
Only **[LTS](https://www.java.com/releases/)** are made available.
{{%/notice %}}

## Binary to use

To use a different version of Java than the default:

- go to **Environment > Java**;
- or use `JAVA_VERSION=[VERSION] java` (replacing `[VERSION]` with the desired Java version).

## Environments|Environment

Your Java environment is initially empty, without any preinstalled libraries.

## HTTP Deployment

To deploy an HTTP application with Java, you need to create a site in the **Web > Sites** section and can use two types of sites:

### Java

It uses the HTTP server [Apache Tomcat](https://tomcat.apache.org/).

{{< fig "images/java-tomcat.png" "">}}

- type: choose _Java_;
- application path: The file path of your Java application.

You can also fill in several optional fields:

- environment variables to be defined;
- a specific Python version to use.

### User Program

[Présentation](sites/user-program)

{{< fig "images/user-program.en.png" "">}}

You will need to specify the command that starts your Java application, for example[^1] :

- [Jenkins](https://www.jenkins.io/doc/book/installing/initial-settings/)

```
$ java -Xmx512m -jar jenkins.war --httpListenAddress=$IP --httpPort=$PORT
```

- [Spring](https://docs.spring.io/spring-boot/docs/current/reference/html/application-properties.html#appendix.application-properties.server)

```
$ java -jar app.jar --server.address=:: --server.port=$PORT
```

{{% notice warning %}}
Your application must not listen on the `::` IP and port specified in the site configuration view under the _Command_ field; or use the IP and PORT environment variables.
{{%/notice %}}

[^1]: Options depend on the app you have to **imped** to check its documentation to find out what options to use if it is necessary to specify the IP and port in the command. This can also be configuration file options.

+++
url = "/en/datasets"
title = "Databases"
pre = "<i class='fas fa-fw fa-database'></i> "
weight = 20
tags = [ "database" ]
+++

The RDBMS (**S**ystems of **G**estion of **B**WIND\*\*) we offer are **entirely info-set**, on all of our offers: we take care of the installation, configuration, maintenance and maintenance of your databases. This way, you only deal with the interactions between your applications and your databases.

- [MariaDB/MySQL](databases/mariadb)
- [PostgreSQL](databases/postgresql)
- [RabbitMQ](databases/rabbitmq)

Private Cloud Plan:

- [ElasticSearch](databases/elasticsearch)
- [Memcached](databases/memcached)
- [Redis](databases/redis)

{{% notice info %}}
For security reasons, creating databases and database users is only possible from the administration interface or from our [API](api). This is therefore not possible by a third-party application (e.g. phpMyAdmin).
{{%/notice %}}

{{% notice warning %}}
It is forbidden to host **only** databases on the free package.
{{%/notice %}}

---

- API resources: [database](https://api.alwaysdata.com/v1/database/doc/), [database user](https://api.alwaysdata.com/v1/database/user/doc/)
- [Duplicate database](databases/duplicate-database)

---
layout: page
title: Architecture technical choices
header: Caliopen Architecture technical choices
group: architecture
category: architecture-category
---
{% include JB/setup %}

## Language and platform

Development language is python for backend and API parts.
Currently only support version >= 2.6 some dependencies are not yet ready for python >= 3.4.

Javascript is used for both client and server side web pages rendering.

## Storage platform

* Main storage platform is [Cassandra](https://cassandra.apache.org)
* Index storage platform is [Elasticsearch](https://www.elastic.co)

* Persistence messaging platform is [RabbitMQ](https://www.rabbitmq.com)
* [Redis](http://redis.io) is used for lighter messaging, objects caching.

## Mail platform

input and output SMTP is done using [postfix](http://www.postfix.org) server.
Components like [DSPAM](http://dspam.sourceforge.net), [Amavis](http://www.amavis.org) are included for basic processing
of RFC2822 messages. Complementary processing is done by doing a LMTP delivery into Caliopen for input messages.

## Infrastructure components

* All inbound TCP flows are done thru one [HAProxy](http://www.haproxy.org) instance using proxy protocol (v2 when possible) with backend service.
* [Docker](https://www.docker.com) containers are used for development purposes, it's not planned to be used in a production setup.
* Deployment tool is at this time [ansible](http://www.ansible.com/home) for it's quick and dirty capability, not sure to keep it for long purposes.
* Monitoring is an open discussion. But it must be easy to integrate configuration at deployment time.

## Python main dependencies

- [datastax cassandra driver](https://github.com/datastax/python-driver) including cqlengine object mapper
- [elasticsearch-dsl](https://github.com/elastic/elasticsearch-dsl-py) for easy ES querying
- [schematics](https://github.com/schematics/schematics) for parameters validation
- [pyramid](http://www.pylonsproject.org) and [cornice](http://cornice.readthedocs.org/en/latest/) for HTTP protocol


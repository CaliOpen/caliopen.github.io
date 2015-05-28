---
layout: architecture-choice
title: Architecture technical choices
header: Caliopen Architecture technical choices
group: navigation
category: architecture-iteration
---

Language and platform
=====================

Development language is python. Currently only support version >= 2.6
some dependencies are not yet ready for python >= 3.4

Parameters validation is done using schematic python package.

Storage platform
================

Main storage platform is Cassandra
Index storage platform is Elasticsearch

Persistence messaging platform is RabbitMQ
Redis is used for lighter messaging, objects caching.

Mail platform
=============

input and output SMTP is done using postfix server.
Components like DSPAM, Amavis are included for basic processing
of RFC2822 messages. Complementary processing is done by doing
a LMTP delivery into Caliopen for input messages.

HTTP Platform
=============

HTTP framework is pyramid and REST API use cornice component.

Infrastructure components
=========================

All inbound TCP flows are done thru one HAProxy instance using
proxy protocol (v2 when possible) with backend service.

Docker containers are used for development purposes, it's not
planned to be used in a production setup.

Deployment tool is at this time ansible for it's quick and dirty
capability, not sure to keep it for long purposes.

Monitoring is an open discussion. But it must be easy to integrate
configuration at deployment time.

Python main dependencies
========================

- datastax cassandra driver including cqlengine object mapper
- elasticsearch-dsl for easy ES querying
- schematics for parameters validation
- pyramid and cornice for HTTP protocol


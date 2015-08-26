---
layout: page
title: Architecture
header: Caliopen Project Architecture
group: navigation
category: architecture-category
---
{% include JB/setup %}

Caliopen is a complete scalable messaging platform. Many components
interacts to complete all services and processes covered by this
platform.

Scalability is merely achieved using data store with such capability,
Cassandra for main storage, elasticsearch for indexing when it have to
be done.

A specific code architecture is defined to make component responsabilities
correctly isolated. Many protocols have to be covered and they aren't related
to an HTTP REST Api in some case.

You can refer to :

* [Code architecture](/architecture/code.html) for software architecture related concepts
* [Technical choices](/architecture/technical_choices.html) for desciption of choosen software
used in CaliOpen platform at this time.
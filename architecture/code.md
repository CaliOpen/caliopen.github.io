---
layout: page
title: Code Architecture
header: Caliopen Code Architecture
group: architecture
category: architecture-category
---
{% include JB/setup %}

## Principles

Caliopen code must respect at least a 3 layers model:

* storage layer
    code responsible for data persistence in all storage engines (cassandra, elasticsearch).
* core layer
    code responsible for all data management methods. Storage is never directly used by
    a caliopen service, they must interact thru core classes related to data managed.
* protocol oriented layer
    code for a specific protocol service. HTTP REST API, LMTP, SMTP are such protocol oriented
    layer.

This layer structure impact on packaging logic to respect split of protocol layer and others, named
base layers. Same data may be managed thru many protocols.

## Packaging

To ensure covering many protocols for many kind of data (contact, message, calendar, file, ...),
Caliopen is decoupled in many python packages. Aim is mainly to limit dependencies for a component
in platform deployment logic, this way a LMTP server will not have pyramid as dependency for example.

There is 2 main type of package:

* base, are defined in this kind of package:
  * storage models classes
  * core classes to manage models
  * input parameters classes
  * return parameters classes

* protocol oriented, where protocol logic act, sometimes only a part of it (API splitted by )

### Base packages

- [caliopen.base](https://github.com/CaliOpen/caliopen.base)
    abstract storage and core classes to be used by all components interacting with data.
    contains also classes for configuration, connection management, common to all components.

- [caliopen.base.user](https://github.com/CaliOpen/caliopen.base.user)
    models and related core classes for user and contact management (an user is also a contact)

- [caliopen.base.message](https://github.com/CaliOpen/caliopen.base.message)
    models and related core classes for messages and threads management

### Protocol oriented packages

- [caliopen.smtp](https://github.com/CaliOpen/caliopen.smtp)
    Package to deliver a SMTP message into caliopen. Use at this time a LMTP server to act as MDA

- [caliopen.api.base](https://github.com/CaliOpen/caliopen.api.base)
    Base package for all Caliopen REST Api ones

- [caliopen.api.user](https://github.com/CaliOpen/caliopen.api.user)
    REST Api to manage users and contacts in a Caliopen instance

- [caliopen.api.message](https://github.com/CaliOpen/caliopen.api.message)
    REST Api to manage messages and thread in a Caliopen instance

- [caliopen.web](https://github.com/CaliOpen/caliopen.web)
    HTTP server with configured REST Api support. Will be deprecated and host only REST API

### Others packages

- [caliopen.cli](https://github.com/CaliOpen/caliopen.cli)
    CLI utility for caliopen management tasks (mainly development ones at this time)

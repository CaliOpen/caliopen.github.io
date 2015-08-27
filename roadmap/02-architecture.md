---
layout: roadmap-item
title: Milestone &#35;2 - Application Architecture
---

The goal of this milestone is to provide all the base components required for
all features.

### Frontend:

Basic services required across all modules, as well as Layout should be
implemented in this milestone. Refer to the [dedicated
doc](https://github.com/CaliOpen/caliopen.frontend/blob/master/doc/01-getting-started.markdown)

* Create Session business service
* Create Authentication business service
* Create Importance business service
* Create Privacy business service
* Layout and basic navigation

### API:

#### Ensure authentication is available through renewable token

In previous milestone, basic authentication features has been developed, and
the authentication strategy has been designed.

This iteration should implement the full authentication mechanism.

#### CRUD Conversations API

Conversation UI/UX is available.

The basic CRUD REST API should be **designed** and **implemented** in this
iteration as it is required for frontend implementation.

This implementation interface should be future proof, but implementation itself
does not need to implement more than e-mail messages.

### UI/UX:

* Cross application interactions (switch application, privacy index...)
* Proposal for List of Conversations UX
* Proposal for Single Conversation UX

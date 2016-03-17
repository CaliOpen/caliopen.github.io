---
layout: page
title: API for creating messages
category: rfc
status: proposal
---
{% include JB/setup %}

This RFC describe the CaliOpen message API requirements to create a new message.

## Resources

Message related resources are **Thread**, **Message**, **MessagePart** and **Recipient**.

A message is created in a `draft` status and then can be identified by its `message_id`
property. If this message is related to a **Thread** then it MUST be created with a
`thread_id` reference.

### Recipients

A recipient MIGHT be related to an known **Contact**. At least a `contact_id` or an `address` MUST
be defined. `protocol` MUST be defined. It is defined by the following informations:

* `contact_id`: Known user contact reference
* `address`: Address to use for sending a message to this recipient
* `protocol`: Communication protocol for this recipient address

### Message

Every new message MIGHT provide the following information:

* `threads`: Reference threads the message is included in. At least one thread MUST be defined.
* `body`: the message body/content/text
* `subject`: Message subject, only apply for mail format
* `attachments`: List of attachments included in the mail

These informations can be updated until message is finalized.

### Threads

* `thread_id`: Reference to the thread.
* `recipients`: List of recipients to send message to

### Attachments

This resource concern attachments that can be included when preparing a new message.

* `message_id`: Message reference this part is related to
* `content_type`: MIME content type for this part
* `data`: Part content

## Questions

* When replying to a thread, recipients are known and MUST NOT be defined.

> Do we need to be able to change the protocol in a thread, yes I guess.

* Does the thread MUST have recipient list and preferred protocol ?

* When adding a new recipient to a message having a thread reference, what happen ?
    ** Create a new thread ?
    ** Include this recipient in current thread ?

> Message MUST NOT add a new recipient to a thread.

* When defining recipient for a new message, it may define which Thread
 this message may relate to.

> I don't get, what's the question ?

* Do we need to allows bcc or cc the message ? Does this will create or attach to a Thread ?

* What about contact creation on the fly like it is described in Recipients section ?

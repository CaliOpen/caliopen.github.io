---
layout: page
title: API for creating messages
category: rfc
status: proposal
---

This RFC describe the CaliOpen message API requirements to create a new message.

## Resources

Message related resources are **Thread**, **Message**, **MessagePart** and **Recipient**.

A message is created in a `draft` status and then can be identified by its `message_id`
property. If this message is related to a **Thread** then it MUST be created with a
`thread_id` reference.

### Recipients

A recipient MIGHT be related to an known **Contact**. It is defined by
the following informations:

* `contact_id`: Known user contact reference
* `address`: Address to use for sending a message to this recipient
* `protocol`: Communication protocol for this recipient address

### Messsage

Every new message MIGHT provide the following information:

* `thread_id`: Reference to the thread the message is included in.
* `body`: the message body/content/text
* `to`: List of recipients to send message to
* `cc`: List of recipients to send a carbon copy of this message
* `bcc`: List of recipients to send a blind carbon copy of this message
* `subject`: Message subject, only apply for mail format
* `attachments`: List of attachments included in the mail

These informations can be updated until message is finalized.

### MessagePart

This resource concern attachments that can be included when preparing a new message.

* `message_id`: Message reference this part is related to
* `content_type`: MIME content type for this part
* `data`: Part content

## Questions

* When replying to a thread, recipients are known and MUST NOT be defined.

* When adding a new recipient to a message having a thread reference, what happen ?
    ** Create a new thread ?
    ** Include this recipient in current thread ?

* When defining recipient for a new message, it may define which Thread
 this message may relate to.

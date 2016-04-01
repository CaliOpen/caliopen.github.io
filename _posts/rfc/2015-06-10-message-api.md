---
layout: page
title: API for messages
category: rfc
status: done
---

This RFC describe the CaliOpen message API requirements to implement current
mockups.

## Resources

> NOTE the field names and structure are here to describe pieces of information.
> Feel free to provide better ones.

> NOTE the term **Link** is used for nested resources. The implementation can
> embed the information OR provide information to retrieve it later (id,
> href...).
>
> If the information is not embedded, then there should be an API endpoint to
> retrieve missing information in batch and prevent too many requests.

Message related resources are **Recipient**, **Thread**, **Attachment** and **Message**.

## Recipient

A recipient MIGHT be related to an known **Contact**. It is defined by
the following informations:

* `contact_id`: Known user contact reference
* `address`: Address to use for sending a message to this recipient
* `protocol`: Communication protocol for this recipient address

## Thread

A **Thread** is a group of **Messages** with additional pieces of information.
Every **Thread** MUST provide the following information:

* `total_count`: the number of messages
* `unread_count`: the number of unread messages
* `subject`: the thread subject. Empty string if none.
* `contacts`: a list of links to contacts involved in the conversation
* `importance_level`: the importance level associated to this conversation
* `privacy_index`: the privacy index associated to this conversation
* `messages`: a list of links to most recent messages. **<--- This is used for
  the thread headline and for the detail view initial display**.
* `attachments`: a list of links to most recent attachments.
* `tags`: a list of tags associated to this conversation.

## Attachment

This resource concern attachment included in a **Message**.

* `message_id`: Message reference this attachment is related to
* `content_type`: MIME content type for this part
* `data`: Part content

## Message

A **Message** can come from several providers (email, twitter, instant chat...).
This is a common abstraction, every message MUST provide the following
information:

* `status`: draft, sending, sent, deleted for outcoming messages. unread, read, deleted 
  for incoming ones.
* `thread`: link to the thread the message is included in.
* `sender`: link to contact who sent this message.
* `recipients`: Recipients involved in this message 
* `sent_at`: date and time the message was sent
* `received_at`: date and time the message was received
* `body`: the message body/content/text
* `type`: the message type
* `importance_level`: the importance level associated to message
* `privacy_index`: the privacy index associated to message
* `payload`: the original message

Every **Message** MIGHT have the following information:

* `subject` the message subject when it exist
* `parent_message`: link to the message this one is a response to

## Requirements

We'll stick to read for now

* List threads, paginated.
* get one thread, messages embedded

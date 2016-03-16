---
layout: page
title: API for messages
category: rfc
status: proposal
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

Message related resources are **Thread** and **Message**.

A **Thread** is a group of **Messages** with additional pieces of information.
Every **Thread** MUST provide the following information:

* `total_count`: the number of messages
* `unread_count`: the number of unread messages
* `subject`: the thread subject. Empty string if none.
* `contacts`: a list of links to contacts involved in the conversation
* `importance_level`: the importance level associated to message
* `privacy_index`: the privacy index associated to message
* `messages`: a list of links to most recent messages. **<--- This is used for
  the thread headline and for the detail view initial display**
* `attachments`: a list of links to most recent attachments.
* `Tags`

A **Message** can come from several providers (email, twitter, instant chat...).
This is a common abstraction, every message MUST provide the following
information:

* `status`: read, draft, unread... **<-- Pleas provide some insight on the way
  you think it should be handled**
* `thread`: link to the thread the message is included in.
* `sender`: link to contact who sent this message if any. **<--- should raw
  information be provided otherwise? It should remain consistent**
* `sent_at`: date and time the message was sent (most probably extracted from
  headers or metadata, depending on the message source)
* `received_at`: date and time the message was received on the CaliOpen platform
* `body`: the message body/content/text
* `origin`: the message source, type or associated account. **<---- Which one is
  the most relevant?**
* `importance_level`: the importance level associated to message
* `privacy_index`: the privacy index associated to message
* `payload`: the original message

Every **Message** MIGHT have the following information:

* `subject` the message subject. **It might differ from conversation <--- I've
  got no idea if this is relevant at this level for anything else than mail
  clients compatibility**
* `parent_message`: link to the message this one is a response to

## Requirements

We'll stick to read for now

* List threads, paginated.
* get one thread, messages embedded

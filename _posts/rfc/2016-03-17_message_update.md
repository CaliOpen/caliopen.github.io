---
layout: page
title: API for updating messages
category: rfc
status: proposal
---
{% include JB/setup %}

This RFC describe the CaliOpen message API requirements to update a message.

## Purpose

A message MIGHT BE marked has read or not. Multiple messages can be updated at the same time.

### Read / Unread

A list of read and unread message_ids MIGHT be sent using the http PATCH  method.
Same id MUST NOT be in both properties.

route: `PATCH /v1/messages/`

body:

```
{
  "read": ["message1", "message2", "message3"],
  "unread": ["message4"]
}
```

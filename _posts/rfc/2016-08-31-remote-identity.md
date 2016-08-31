---
layout: page
title: API remote identity
category: rfc
status: proposal
---

{% include JB/setup %}

This RFC describe how to manage remote identity

## Purpose

A `remote identity` determines how a third party messaging plateform is connected in order to fetch
and send private communications.

## Schema

Remote Identity MUST be rendered in the required content-type, generally `json`.

route: `GET v1/remote-identities`

```json
{
  "remote_identities": [
    {
      "remote_identity_id": "0ba2e346-e4f8-4c45-9adc-eeb1d42f07e2",
      "is_fetching": true,
      "connected": false,
      "last_connection": "2016-08-31T10:15:39+0200",
      "connection_required": true,
      "cancel_fetch_required": false,
      "identity_type": "email",
      "params": {
        "login": "foo",
        "password": "bar",
        "mail_protocol": "IMAP",
        "incomming_mail_server": "imap.bar.tld",
        "mail_port": "993",
        "fetch_method": "from_now"
      }
    }
  ],
  "total": 1
}
```

### Details

 * is_fetching: calculated by the API, a fetching operation is running
 * connected: calculated by the API, the result state of the last connection attempt
 * connection_required: user asked to connect
 * cancel_fetch_required: user asked to cancel fetching
 * identity_type: determine witch contact sub-object to use, can be one of ['email', 'im', 'social_identitiy']
 * identity_id: the sub-object id
 * params: an "free" with the properties required by the third party plateform
 * custom param entries:
   * mail_protocol: standard `IMAP` or `POP` are allowed; `gmail` can be also a valid entry

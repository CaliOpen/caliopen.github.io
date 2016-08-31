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
      "identity_id": "92d3727a-eefc-4537-b879-85f1c9d197bb",
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
 * identity_type: determine witch contact sub-object to use, can be one of ['email', 'im',
 'social_identitiy']
 * identity_id: the sub-object id
 * params: an "free" with the properties required by the third party plateform, the sub-object of
 contact will determine what kind of provider will be used

## Specific notes

**Gmail** is a bit special because it is a mail that can be connected by IMAP, POP and its API.
Also personnal and company addresses can be used with this provider eg. `foo@bar.tld`.

When using this API, the client has to update the contact sub-object `provider` property:

* PUT /contacts/{user.contact.contact_id}/emails/{email_id}

```
{
  email: {
    address: 'bender@planet-express.fake',
    date_insert: '2016-05-25T14:13:05.591000',
    is_primary: 1,
    label: null,
    type: 'home',
    provider: 'gmail'
  },
}
```

---
layout: page
title: API errors schema
category: rfc
status: proposal
---

{% include JB/setup %}

This RFC describe how errors are rendered by CaliOpen API.

## Purpose

Errors must feet to multiple situations:

* request for **getting**, **modifying** or **deleting** resources
* errors witch are **generic**, **property specific** or both
* request that depend on **authenticated** user (HTTP status code 401)
* request that depend on **authorized** user (HTTP status code 403)
* request that generate an **internal server error** (HTTP status code 500)

## Schema

Errors MUST be rendered in the required content-type, generally `json`.

```json
{
  "errors": [
    {
      "description": "string",
      "type": "string",
      "values": ["string"],
      "property": "string",
      "component": "string",
      "code": "string"
    }
  ]
}
```

### Error

* An Error MUST have a description in English (eg. `The login is not available`)
* An Error MUST be typed (the kind of error, eg. `max-len`, `internal`)
* An Error MAY have one or more values depends on type (eg. for error `max`, value: `6`)

#### Property

In a modifying request (POST, PUT or PATCH), an Error MAY have a `property` that represents an invalid resource property.

A property MIGHT be a sub-property. In that case its path should be represented separated by dots `.`.

eg:

* `address.zip_code`
* `contacts.azehgsqf-sdmlf45lk-alzmd.name`


#### Values

Values depends of the type of the error, here is a sample:

| error type | value type | description |
|------------|------------|-------------|
| type       | string     | unexpected type [integer, float, string, bool ...] |
| min        | float      | min value authorized for a number |
| max        | float      | max value authorized |
| min-len    | integer    | min length authorized for a string or an array |
| ...        | ...        | ...         |

#### Component

In case of an internal server error (HTTP status code 5xx), an Error SHOULD have a `component` property representing the python component (eg. `caliopen.base.message`).

#### Code

In case of an internal server error (HTTP status code 5xx), an Error SHOULD have a `code` witch will MIGHT be rendered to the end-user, in order to alert the provider of the current caliopen instance.

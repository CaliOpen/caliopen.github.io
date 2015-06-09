---
layout: page
title: RFC
group: navigation
tagline: What needs to be done
---
{% include JB/setup %}

**CaliOpen** relies on RFCs for feature implementations. It ensure we all agreed
on what needs to be done.

To create a new RFC, follow the [guide]({{site.url}}/guides/create-a-rfc.html).

## Waiting For Implementation

{% for rfc in site.categories.rfc %}
    {% if rfc.status == 'accepted' or rfc.status == 'proposal' %}
* [{{ rfc.title }}]({{rfc.url}})
    {% endif %}
{% endfor %}

## Accomplished Tasks

{% for rfc in site.categories.rfc %}
    {% if rfc.status == 'done' %}
* [{{ rfc.title }}]({{rfc.url}})
    {% endif %}
{% endfor %}


---
layout: page
title: Create a RFC
category: guides
---

First, fork the [caliopen.github.io
repository](https://github.com/CaliOpen/caliopen.github.io) in your own
namespace.

Create a `_posts/rfc/YYY-MM-DD-title-daserized.md` file, where **YYYY** is the
current year (4 digits), **MM** is the current month (2 digits) and **DD** is
the current day (2 digits).

Add this content:

    ---
    title: Describe your RFC
    category: rfc
    status: proposal
    ---

    Add the content for your RFC in here

A rfc can have the following status:

* proposal
* validated
* done

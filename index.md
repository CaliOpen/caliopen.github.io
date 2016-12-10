---
layout: page
title: CaliOpen Dev
tagline: Be Good
---
{% include JB/setup %}

Welcome to the [CaliOpen](https://caliopen.org) development community.

**Want to play with our Proof Of Concept?**

![GUI](/assets/images/play_with_poc.png)

Go to [poc.caliopen.org](https://poc.caliopen.org/) and login with `john@mail.caliopen.me`, password `123456`.

_(Caliopen POC instance is regularly updated and might be broken)_

## Contribute

Help is welcome.

To contribute to a CaliOpen project, you MUST follow the
[contribute guide](/guides/contribute.html)

## Getting Started

The development entrypoint is [CaliOpen
dev](https://github.com/CaliOpen/CaliOpen) repository.

The bug tracker is available in [CaliOpen/Caliopen](https://github.com/CaliOpen/Caliopen/issues).

### Requirements

* [Virtualbox](https://virtualbox.org)
* [Vagrant](https://vagrantup.com)

Once you have vagrant and virtualbox installed, you can launch an development platform
issuing theses commands:

```
cd devtools
vagrant up
```

Are installed in this vm:

- Cassandra, Elasticsearch, Redis storage services run in this VM
- a CaliOpen LMTP server listen on port 4025 for mail delivery
- a CaliOpen ReSt API server listen on port 6543
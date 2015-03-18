---
layout: page
title: CaliOpen Dev
tagline: Be Good
---
{% include JB/setup %}

Welcome to the [CaliOpen](https://caliopen.org) development community.

## Contribute

Help is welcome.

To contribute to a CaliOpen project, you MUST follow the
[contribute guide](/guides/contribute.html)

## Getting Started

The development entrypoint is [CaliOpen
dev](https://github.com/CaliOpen/caliopen-dev) repository.

### Requirements

* [Docker](https://docker.com/)
* [Docker compose](https://docs.docker.com/compose/) ex fig
* python 2.7
* python-dev (debian package, or your distribution equivalent)
* virtualenv (debian package, or your distribution equivalent)
* libffi-dev (debian package, or your distribution equivalent)

### Install

{% highlight bash %}
# Create CaliOpen workdir
mkdir caliopen && cd $_

# Clone development utilities
git clone https://github.com/CaliOpen/caliopen-dev.git bin

# Set up development environment
./bin/install
{% endhighlight %}

Report to [installation
instructions](https://github.com/CaliOpen/caliopen-dev#caliopen-development-environment-and-toolbelt)
for further informations.

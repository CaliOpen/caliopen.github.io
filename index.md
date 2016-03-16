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

The bug tracker is available in [CaliOpen/Caliopen](https://github.com/CaliOpen/Caliopen/issues).

### Requirements

* [Docker](https://docker.com/)
* [Docker compose](https://docs.docker.com/compose/) ex fig

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

### Run

By default the start command run CaliOpen in development environment. The staging environment can be launched with the following command:

{% highlight bash %}
# Start or restart in staging environment
ENV=staging ./bin/start

# Start or restart in development environment
./bin/start

# Stop
./bin/stop
{% endhighlight %}

This use docker-compose, so you can see status of Caliopen:

{% highlight bash %}
cd bin/
docker-compose ps
{% endhighlight %}

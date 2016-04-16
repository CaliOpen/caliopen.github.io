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

The first time you run `start` comand it will build all the containers from scratch, it can be a bit long. Afterward you will be able to load some fixtures.

{% highlight bash %}
# Start caliopen containers
./bin/start

# load a fake user
./bin/load-fixtures
{% endhighlight %}

The server is now up on your machine on http://localhost:4000/.
You will be able to connect with `julien.muetton@gandi.net` and `123456`.

### Tips

By default the `start` command run CaliOpen in development environment. The staging environment can be launched with the following command:

{% highlight bash %}
# Start or restart in staging environment
ENV=staging ./bin/start

# Start or restart in development environment
./bin/start

# Stop all CaliOpen running containers
./bin/stop
{% endhighlight %}

This uses docker-compose, so you can see status of Caliopen and its logs for each containers:

{% highlight bash %}
cd bin/
docker-compose ps
docker-compose logs
{% endhighlight %}

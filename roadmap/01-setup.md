---
layout: roadmap-item
title: Milestone &#35;1 - Setup
---

The goal of this milestone is to setup the project environment and ease user
contributions.

Associated trello board can be found
[here](https://trello.com/b/cdTlFmyN/caliopen)


### Easy install/bootstrap

- Add a script to install the whole stack easily.
- The documentation is updated to reflect this process.
- On [CaliOpen.org](https://caliopen.org/) all links to **caliopen.web** should
  be updated to link to [caliopen-dev
  repository](https://github.com/CaliOpen/caliopen-dev)

### Setup the frontend environment to be served by web server

Frontend environment should be served by the python webserver.

### Setup User Authentication

For performance reasons, user authentication page is provided by the server.

SPA can provide a user authentication too, but when a user first arrives on a
CaliOpen pod, the authentication page is a pure static page.

API calls are protected thanks to a token. The whole security protocol is still
**to be defined**.

Frontend code uses a dedicated service to store authentication.

Backend provides a way to manage authentication:

* log user in
* get token
* refresh token
* revoke token

### Bootstrap frontend code

Frontend code uses [emberjs](http://emberjs.com/) and
[ember-cli](http://www.ember-cli.com/)

Documentation and frontend project architecture are stored in the project [doc
folder](https://github.com/CaliOpen/caliopen.frontend/tree/master/doc).

Frontend leverages travis-ci for continuous integration.

### Prepare Plan

This iteration should prepare further milestones and define a way to organize
work. Github issues seems a great place to start.

### cleaning ?

Once the backend organization is done, old repositories should be (re)moved.


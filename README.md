# docker-ikiwiki
## Overview
This is dockerfile for building a dockerized ikiwiki server.
Ikiwiki is git backend based wiki engine.
You can find more information on ikiwiki [here](https://ikiwiki.info/)

The docker image is based on debian/jessie, the web server used is lighttpd.
A ssh server will also be started in order to be able to use the git workflow with ikiwiki.
The ssh sever is accessible with the user www-data (same password than login).
A volume is required to make the initial repository import a local repository.

## How to build the image
You can use this command:

``
docker build -t ikiwiki:latest .
``

## How to run the container
``
docker run -v <local git repository>:/wiki -p 2222:22 -p 8080:80 ikiwiki:latest
``

The container can also be run from the pre-built image on [docker hub](https://hub.docker.com/r/dgsb/ikiwiki/) with this command:

``
docker run -v <local git repository>:/wiki -p 2222:22 -p 8080:80 dgsb/ikiwiki
``

The wiki server will be accessible through:

``
http://127.0.0.1:8080
``

You can add a remote on your local git repository:

``
git remote add docker ssh://www-data@127.0.0.1:2222/var/wwww/wiki.git
``


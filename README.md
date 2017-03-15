# Docker Phalcon

[![](https://images.microbadger.com/badges/version/gabel/phalcon:7.0-fpm.svg)](http://microbadger.com/images/gabel/phalcon:7.0-fpm "Get your own version badge on microbadger.com") [![](https://images.microbadger.com/badges/image/gabel/phalcon:7.0-fpm.svg)](http://microbadger.com/images/gabel/phalcon:7.0-fpm "Get your own image badge on microbadger.com")  [![](https://img.shields.io/docker/stars/gabel/phalcon.svg)](https://hub.docker.com/r/gabel/phalcon/)  [![](https://img.shields.io/docker/pulls/gabel/phalcon.svg)](https://hub.docker.com/r/gabel/phalcon/)

Forked from mileschou docker phalcon base image, see https://hub.docker.com/r/mileschou/phalcon/

The repository is a Docker image based on [Docker official PHP image](https://hub.docker.com/_/php/) with [Phalcon Framework](https://phalconphp.com/) Version 3.0+.

## Supported tags and respective `Dockerfile` links

* [`7.0-fpm`, `fpm` (7.0/fpm/Dockerfile)](https://github.com/gabel/phalcon/blob/master/7.0/fpm/Dockerfile)

## Image Test

Here is a simple test command that can confirm the extension has been loaded.

    $ docker run -i -t --rm mileschou/phalcon php -m | grep phalcon
    phalcon

## Phalcon Devtools CLI

The repository also include [Phalcon Devtools](https://github.com/phalcon/phalcon-devtools). Here is a simple command.

    $ docker run -i -t --rm mileschou/phalcon phalcon

    Phalcon DevTools (3.0.0)

    Available commands:
      commands         (alias of: list, enumerate)
      controller       (alias of: create-controller)
      module           (alias of: create-module)
      model            (alias of: create-model)
      all-models       (alias of: create-all-models)
      project          (alias of: create-project)
      scaffold         (alias of: create-scaffold)
      migration        (alias of: create-migration)
      webtools         (alias of: create-webtools)

## Build yourself

Recommend 2G+ RAM when build image yourself. Maybe wait a long time for compile if only 1G RAM.

## Thanks

* [GitHub](https://github.com/)
* [Docker Hub](https://hub.docker.com/)
* [Shields.io](https://img.shields.io/) provide docker hub stars and pulls badge
* [MicroBadger](https://microbadger.com/) provide image size and version badge
* [maestrooo](https://github.com/maestrooo/eb-docker-php7) docker aws elastic beanstalk multicontainer defaults
* [MilesChou](https://github.com/MilesChou/docker-phalcon) Docker-phalcon base image 
# Docker

`docker run --name my-nginx -d -v /Users/adibnoh/Docker/my-nginx/nginx.conf:/etc/nginx/nginx.conf:ro -v /Users/adibnoh/Docker/my-nginx/src:/usr/share/nginx/html:ro -p 80:80 nginx:1.14.1`

## Docker Hub

[https://hub.docker.com/](https://hub.docker.com/)

## Tutorial

* [Getting started with docker, the step by step tutorial](https://www.youtube.com/watch?v=Vyp5_F42NGs)

## Dockerfile

Enter your working directory and create file `Dockerfile` without any extension

`cd <working_directory> && touch Dockerfile`

Edit your `Dockerfile`, `nano Dockerfile` - you can follow below sample

```Dockerfile

FROM alpine:3.4
MAINTAINER Adib Noh bromatrik@gmail.com

RUN apk update curl vim git

```

After finish editing, you may run a command to build Docker Image using `Dockerfile` you just created.

`docker build -t <creator_name>/<package_name>:<version_number> <Dockerfile_location>` - preferable syntax

`docker build -t adib/my-alpine:1.0 .` - example

### Dockerfile Syntax

`FROM`

`MAINTAINER`

`COPY`

`RUN`

### Dockerfile Cleanup

Every time you build your `Dockerfile` you will create Docker Image cache in your system. Normally this cache will cause no harm, but every time you've made changes to your Dockerfile and rebuild it, it will create dangling image cache from previous build that is unusable. To remove all dangling image cache you may run this command

`docker rmi $(docker images -q --filter "dangling=true")`

## Run Docker

`docker run [OPTIONS] IMAGE[:TAG|@DIGEST] [COMMAND] [ARG...]`

Interactive mode - `-ti`

Remove from containers after exit - `--rm`
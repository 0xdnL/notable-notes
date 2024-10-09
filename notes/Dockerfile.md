---
tags: [container]
title: Dockerfile
created: '2024-02-08T12:22:45.265Z'
modified: '2024-10-08T09:22:15.749Z'
---

# Dockerfile

## usage

```sh
ARG           # Use build-time variables
ONBUILD       # Specify instructions for when the image is used in a build

LABEL         # Add metadata to an image
MAINTAINER    # Specify the author of an image (deprecated ?)

FROM          # Create a new build stage from a base image

ADD           # Add local or remote files and directories
COPY          # Copy files and directories

CMD           # Specify default commands
ENTRYPOINT    # Specify default executable

ENV           # Set environment variables

EXPOSE        # Describe which ports your application is listening on
              # https://forums.docker.com/t/what-is-the-use-of-expose-in-docker-file/37726/2

VOLUME        # Create volume mounts

HEALTHCHECK   # Check a container's health on startup

SHELL         # Set the default shell of an image
STOPSIGNAL    # Specify the system call signal for exiting a container

RUN           # Execute build commands
USER          # Set user and group ID
WORKDIR       # Change working directory
```

## example

```yaml
# syntax=docker/dockerfile:1

FROM ubuntu:22.04
COPY . /app
RUN make /app
CMD python /app/app.py
```

## see also

- [[docker-compose]]
- [[docker]]
- [[buildah]], [[executor]]
- [docs.docker.com/engine/reference/builder/](https://docs.docker.com/engine/reference/builder/)

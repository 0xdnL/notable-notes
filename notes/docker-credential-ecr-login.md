---
title: docker-credential-ecr-login
created: '2024-11-16T05:10:25.277Z'
modified: '2024-11-16T05:13:16.059Z'
---

# docker-credential-ecr-login

> amazon ecr docker credential helper is a credential helper for docker daemon making it easier to use aws ecr

## install

bundled with [[rdctl]]

## usage

```sh
docker-credential-ecr-login store
docker-credential-ecr-login get
docker-credential-ecr-login erase
docker-credential-ecr-login list
docker-credential-ecr-login version

docker-credential-ecr-login -v   # print version and exit
```

## see also

- [github.com/awslabs/amazon-ecr-credential-helper](https://github.com/awslabs/amazon-ecr-credential-helper)

---
tags: [crypto]
title: gpg-agent
created: '2023-09-18T07:26:21.112Z'
modified: '2023-11-21T15:50:57.102Z'
---

# gpg-agent

> daemon to manage secret (private) keys independently from any protocol. It is used as a backend for [[gpg]]

## install

```s
brew install gpg2
```

## env

```sh
GPG_TTY
```

## gpg-agent.conf

```sh
default-cache-ttl 3600
max-cache-ttl 7200
```

## usage

```sh
gpg-agent
```

## see also

- [[git]]
- [[gpg]]
- [[ssh]]
- [[ssh-agent]]

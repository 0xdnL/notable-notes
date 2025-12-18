---
title: valkey-cli
created: '2025-10-28T12:28:45.955Z'
modified: '2025-11-06T14:46:40.524Z'
---

# valkey-cli

[[redis-cli]] [[NoSQL]]

## install

```sh
brew install valkey

docker run -e VALKEY_PASSWORD=password123 -p 6379:6379 bitnami/valkey:latest
```

## usage

```sh
valkey-cli -a password123

# Using URI form:
valkey-cli -u valkey://default:password123@valkey-primary.NAMESPACE.svc.cluster.local:6379/0 
```

## ACL

> [valkey.io/commands/acl/](https://valkey.io/commands/acl/)

```sh
127.0.0.1:6379> ACL WHOAMI

127.0.0.1:6379> ACL GETUSER default
```

## SET/GET

> SET key value [valkey.io/commands/set](https://valkey.io/commands/set/)
> GET key value [valkey.io/commands/get](https://valkey.io/commands/get/)

```sh
127.0.0.1:6379> SET user:1000 "Alice"
OK
127.0.0.1:6379> GET user:1000
"Alice"
```


## see also

- [[kubectl]]

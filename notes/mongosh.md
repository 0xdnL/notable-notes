---
tags: [database/mongodb]
title: mongosh
created: '2021-09-07T07:21:44.793Z'
modified: '2026-01-29T01:06:55.590Z'
---

# mongosh

> [[node]] REPL environment for interacting with mongodb

## install

```sh
brew install mongosh
```

## usage

```sh
mongosh --port 28015      # connects to instance running on localhost with a non-default port

mongosh mongodb://user:pass@mongodb
```

## repl

```sh
> show dbs;
```

## see also
 
- [[mongo]]

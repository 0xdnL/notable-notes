---
tags: [database]
title: pgenv
created: '2023-11-17T12:30:24.512Z'
modified: '2023-12-19T15:00:33.950Z'
---

# pgenv

> simple utility to build and run different releases of [[psql]]

## install

```sh
git clone https://github.com/theory/pgenv.git ~/.pgenv
echo 'export PATH="$HOME/.pgenv/bin:$HOME/.pgenv/pgsql/bin:$PATH"' >> ~/.bash_profile
```

## usage

```sh
pgenv build 15.0 && pgenv use 15.0
```

## see also

- [[pgsql]]
- [[pg_activity]]
- [[tfswitch]]
- [github.com/theory/pgenv](https://github.com/theory/pgenv)

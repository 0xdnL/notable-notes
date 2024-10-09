---
tags: [python, sql]
title: mssql-cli
created: '2024-09-22T11:18:51.260Z'
modified: '2024-09-22T11:25:55.669Z'
---

# mssql-cli

>  interactive cli query tool for mssql server

## install

```sh
python -m pip install mssql-cli
```

## usage

```sh
mssql-cli -S HOST -d DATABASE -U USERNAME -P PASSWORD
```


## shell

```sql
master> \?            ; get help

master> use master

master> \lt SCHEMA
```

## see also

- [[sqlcmd]]
- [[mysql]]

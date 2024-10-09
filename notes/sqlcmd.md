---
tags: [go, sql]
title: sqlcmd
created: '2024-09-22T11:15:43.865Z'
modified: '2024-09-30T10:08:49.904Z'
---

# sqlcmd

> cli for mssql server and azure sql

## install

```sh
curl https://packages.microsoft.com/keys/microsoft.asc | sudo tee /etc/apt/trusted.gpg.d/microsoft.asc
add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/20.04/prod.list)"
apt-get update
apt-get install sqlcmd
```

## usage

```sh
sqlcmd -S HOSTNAME -U USERNAME -P PASSWORD -d master -i setup.sql -C
```

## interactive mode

```sql
1> select DB_NAME()  -- list current database
2> GO

1> select name from sys.databases  -- list databases
2> go

1> Sp_databases   -- used stored procedure to list databases
2> go

1> SELECT SERVERPROPERTY('COLLATION')
2> GO
--------------------------------------------------
SQL_Latin1_General_CP1_CI_AS    -- CI: Case Insensitive, CS: Case Sensitive, AS: Accent Sensitive, AI: Accent Insensitive


1> SELECT SERVERPROPERTY('EDITION')   -- check the SQL Server Edition
2> go

1> SELECT SERVERPROPERTY('IsIntegratedSecurityOnly')    --  check the SQL Server Authentication
2> go
-- 0: both SQL Server Account and Windows authentications are enabled
-- 1: only Windows Authentication is enabled
```

## commands

```sql
1> :ListVar
```

## see also


- [[mssql-cli]]
- [[mysql]]
- [[psql]]
- [github.com/microsoft/go-sqlcmd](https://github.com/microsoft/go-sqlcmd)

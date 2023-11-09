---
tags: [database, linux]
title: psql
created: '2019-07-30T06:19:49.220Z'
modified: '2023-11-07T13:33:04.416Z'
---

# psql

> postgresql - object-relational database management system written in [[c]]

## install

```sh
apt install postgresql

brew install postgresql@14
brew services start postgresql@14                                                       # start postgresql@14 service
$HOMEBREW_PREFIX/opt/postgresql@14/bin/postgres -D $HOMEBREW_PREFIX/var/postgresql@14   # start background service directly

docker run -ti --rm -e POSTGRES_PASSWORD=password postgres psql -U postgres
```

## usage

```sh
psql DBNAME USER

psql DBNAME -U USER -d DATABASE

psql -U USER -d DATABASE -c "SELECT * FROM some_table"

psql -h HOST -p 5432 -U postgres
```

## console

```sql
\?                -- help for psql commands
\h                -- help for SQL commands

\conninfo         -- information about the current database connection

\list             -- list all databases

\c       DATABASE -- connect to database
\connect DATABASE -- connect to database

\dt               -- list all tables in current database
\dn               -- list all schema in current database

\z                -- list all of the tables, views, and sequences in the database

\q                -- exit the psql program

\d+ table         -- describe
DESCRIBE TABLE

\x auto         -- output format

select version();   -- get server version
```

```sql
-- init
CREATE DATABASE bookstore;
CREATE USER bookstore_user WITH ENCRYPTED PASSWORD 'secret';
GRANT ALL PRIVILEGES ON DATABASE bookstore TO bookstore_user;
GRANT ALL PRIVILEGES ON TABLE books TO bookstore_user;

psql "dbname=bookstore host=localhost user=bookstore_user password=secret port=5432"
sslmode=require


BEGIN; UPDATE users SET admin = 't' WHERE id = '38'; select admin from users where id = '38'; ROLLBACK; -- dryrun


SELECT pg_size_pretty( pg_database_size('DATABASE') );    -- get db size
```

## see also

- [[pg_dump]]
- [[mysql]]
- [[mongo]]
- [postgresql.org/docs/current](https://www.postgresql.org/docs/current/index.html)
- [PSQL-META-COMMANDS](https://www.postgresql.org/docs/current/static/app-psql.html#APP-PSQL-META-COMMANDS)
- [alternate-output-format-for-psql](https://stackoverflow.com/questions/9604723/alternate-output-format-for-psql)


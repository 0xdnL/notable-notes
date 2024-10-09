---
tags: [database/postgresql]
title: pgbadger
created: '2024-05-06T12:23:12.776Z'
modified: '2024-10-08T09:23:00.074Z'
---

# pgbadger

>  postgresql log analyzer with fully detailed reports and graphs

## usage

```sh
pgbadger ./postgresql-1.csv

pgbadger /var/log/postgresql.log
pgbadger /var/log/postgres.log.2.gz /var/log/postgres.log.1.gz /var/log/postgres.log
pgbadger /var/log/postgresql/postgresql-2012-05-*

pgbadger --exclude-query="^(COPY|COMMIT)" /var/log/postgresql.log

pgbadger -b "2012-06-25 10:56:11" -e "2012-06-25 10:59:11" /var/log/postgresql.log

cat /var/log/postgres.log | pgbadger -

# Log line prefix with stderr log output
pgbadger --prefix '%t [%p]: user=%u,db=%d,client=%h' /pglog/postgresql-2012-08-21*
pgbadger --prefix '%m %u@%d %p %r %a : ' /pglog/postgresql.log

# Log line prefix with syslog log output
pgbadger --prefix 'user=%u,db=%d,client=%h,appname=%a' /pglog/postgresql-2012-08-21*

# Use my 8 CPUs to parse my 10GB file faster, much faster
pgbadger -j 8 /pglog/postgresql-10.1-main.log
```

## see also

- [[psql]]
- [[perl]]
- [github.com/darold/pgbadger](https://github.com/darold/pgbadger)

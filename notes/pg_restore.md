---
tags: [database/postgresql]
title: pg_restore
created: '2023-11-16T13:16:38.100Z'
modified: '2023-11-18T13:26:29.009Z'
---

# pg_restore

> pg_restore restores a PostgreSQL database from an archive created by [[pg_dump]]

## usage

```sh
pg_restore                      -U username -d dbname -1 filename.dump
pg_restore -h localhost -p 5432 -U postgres -d old_db -v "/usr/local/backup/10.70.0.61.backup"
```

## see also

- [[pg_dump]]
- [[pg_dumpall]]
- [[psql]]
- [[mysqldump]]
- [[mongodump]]
- [postgresql.org/docs/9.0/libpq-envars](https://www.postgresql.org/docs/9.0/libpq-envars.html)

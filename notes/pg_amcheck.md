---
tags: [database/postgresql]
title: pg_amcheck
created: '2024-07-29T13:14:54.777Z'
modified: '2024-10-08T09:23:00.095Z'
---

# pg_amcheck

> pg_amcheck checks objects in a PostgreSQL database for corruption

## options

```sh
# Target options:
  -a, --all                       # check all databases
  -d, --database=PATTERN          # check matching database(s)
  -D, --exclude-database=PATTERN  # do NOT check matching database(s)
  -i, --index=PATTERN             # check matching index(es)
  -I, --exclude-index=PATTERN     # do NOT check matching index(es)
  -r, --relation=PATTERN          # check matching relation(s)
  -R, --exclude-relation=PATTERN  # do NOT check matching relation(s)
  -s, --schema=PATTERN            # check matching schema(s)
  -S, --exclude-schema=PATTERN    # do NOT check matching schema(s)
  -t, --table=PATTERN             # check matching table(s)
  -T, --exclude-table=PATTERN     # do NOT check matching table(s)
      --no-dependent-indexes      # do NOT expand list of relations to include indexes
      --no-dependent-toast        # do NOT expand list of relations to include TOAST tables
      --no-strict-names           # do NOT require patterns to match objects

# Table checking options:
      --exclude-toast-pointers    # do NOT follow relation TOAST pointers
      --on-error-stop             # stop checking at end of first corrupt page
      --skip=OPTION               # do NOT check "all-frozen" or "all-visible" blocks
      --startblock=BLOCK          # begin checking table(s) at the given block number
      --endblock=BLOCK            # check table(s) only up to the given block number

# B-tree index checking options:
      --heapallindexed            # check that all heap tuples are found within indexes
      --parent-check              # check index parent/child relationships
      --rootdescend               # search from root page to refind tuples

# Connection options:
  -h, --host=HOSTNAME             # database server host or socket directory
  -p, --port=PORT                 # database server port
  -U, --username=USERNAME         # user name to connect as
  -w, --no-password               # never prompt for password
  -W, --password                  # force password prompt
      --maintenance-db=DBNAME     # alternate maintenance database

# Other options:
  -e, --echo                      # show the commands being sent to the server
  -j, --jobs=NUM                  # use this many concurrent connections to the server
  -P, --progress                  # show progress information
  -v, --verbose                   # write a lot of output
  -V, --version                   # output version information, then exit
      --install-missing           # install missing extensions
  -?, --help                      # show this help, then exit
```

## usage

```sh
pg_amcheck -U postgres -h localhost --all
```

## see also

- [[psql]]

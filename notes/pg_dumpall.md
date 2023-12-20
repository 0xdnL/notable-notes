---
tags: [database/postgresql]
title: pg_dumpall
created: '2023-11-16T13:09:53.277Z'
modified: '2023-11-18T13:26:29.014Z'
---

# pg_dumpall

> extracts a PostgreSQL database cluster into an SQL script file

## environment

```sh
PGDATABASE        # -
PGHOST            # -
PGOPTIONS         # -
PGPORT            # -
PGUSER            # -
PGSSLMODE         # determines whether or with what priority a secure SSL TCP/IP connection will be negotiated with the server. There are six modes:
                  #   disable 	    only try a non-SSL connection
                  #   allow 	      first try a non-SSL connection; if that fails, try an SSL connection
                  #   prefer        (default) 	first try an SSL connection; if that fails, try a non-SSL connection
                  #   require 	    only try an SSL connection. If a root CA file is present, verify the certificate in the same way as if verify-ca was specified
                  #   verify-ca 	  only try an SSL connection, and verify that the server certificate is issued by a trusted CA
                  #   verify-full 	only try an SSL connection, verify that the server certificate is issued by a trusted CA and that the server host name matches that in the certificate
```

## option

```sh
-f, --file=FILENAME               # output file name
-v, --verbose                     # verbose mode
-V, --version                     # output version information, then exit
    --lock-wait-timeout=TIMEOUT   # fail after waiting TIMEOUT for a table lock
-?, --help                        # show this help, then exit

# controlling the output content
-a, --data-only                     # dump only the data, not the schema
-c, --clean                         # clean (drop) databases before recreating
-E, --encoding=ENCODING             # dump the data in encoding ENCODING
-g, --globals-only                  # dump only global objects, no databases
-O, --no-owner                      # skip restoration of object ownership
-r, --roles-only                    # dump only roles, no databases or tablespaces
-s, --schema-only                   # dump only the schema, no data
-S, --superuser=NAME                # superuser user name to use in the dump
-t, --tablespaces-only              # dump only tablespaces, no databases or roles
-x, --no-privileges                 # do not dump privileges (grant/revoke)
    --binary-upgrade                # for use by upgrade utilities only
    --column-inserts                # dump data as INSERT commands with column names
    --disable-dollar-quoting        # disable dollar quoting, use SQL standard quoting
    --disable-triggers              # disable triggers during data-only restore
    --exclude-database=PATTERN      # exclude databases whose name matches PATTERN
    --extra-float-digits=NUM        # override default setting for extra_float_digits
    --if-exists                     # use IF EXISTS when dropping objects
    --inserts                       # dump data as INSERT commands, rather than COPY
    --load-via-partition-root       # load partitions via the root table
    --no-comments                   # do not dump comments
    --no-publications               # do not dump publications
    --no-role-passwords             # do not dump passwords for roles
    --no-security-labels            # do not dump security label assignments
    --no-subscriptions              # do not dump subscriptions
    --no-sync                       # do not wait for changes to be written safely to disk
    --no-tablespaces                # do not dump tablespace assignments
    --no-toast-compression          # do not dump TOAST compression methods
    --no-unlogged-table-data        # do not dump unlogged table data
    --on-conflict-do-nothing        # add ON CONFLICT DO NOTHING to INSERT commands
    --quote-all-identifiers         # quote all identifiers, even if not key words
    --rows-per-insert=NROWS         # number of rows per INSERT; implies --inserts
    --use-set-session-authorization # use SET SESSION AUTHORIZATION commands instead of ALTER OWNER commands to set ownership

# connection options
-d, --dbname=CONNSTR        # connect using connection string
-h, --host=HOSTNAME         # database server host or socket directory
-l, --database=DBNAME       # alternative default database
-p, --port=PORT             # database server port number
-U, --username=NAME         # connect as specified database user
-w, --no-password           # never prompt for password
-W, --password              # force password prompt (should happen automatically)
    --role=ROLENAME         # do SET ROLE before dump
```

## usage

```sh
pg_dumpall --roles-only
```

## see also

- [[pg_dumpall]]
- [[psql]]
- [[mysqldump]]
- [[mongodump]]
- [postgresql.org/docs/9.0/libpq-envars](https://www.postgresql.org/docs/9.0/libpq-envars.html)

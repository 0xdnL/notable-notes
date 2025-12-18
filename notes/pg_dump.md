---
tags: [database/postgresql, python]
title: pg_dump
created: '2021-03-15T07:59:51.829Z'
modified: '2025-11-21T12:33:33.639Z'
---

# pg_dump

> extract a postgresql database into a script file or other archive file

[[pg_dumpall]], [[pg_restore]]

## install

```sh
```

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
# General options
-f, --file=FILENAME               # output file or directory name
-F, --format=c|d|t|p              # output file format (custom, directory, tar, plain text (default))
-j, --jobs=NUM                    # use this many parallel jobs to dump
-v, --verbose                     # verbose mode
-V, --version                     # output version information, then exit
-Z, --compress=0-9                # compression level for compressed formats
    --lock-wait-timeout=TIMEOUT   # fail after waiting TIMEOUT for a table lock
    --no-sync                     # do not wait for changes to be written safely to disk
-?, --help                        # show this help, then exit

# Options controlling the output content
-a, --data-only                       # dump only the data, not the schema
-b, --blobs                           # include large objects in dump
-B, --no-blobs                        # exclude large objects in dump
-c, --clean                           # clean (drop) database objects before recreating
-C, --create                          # include commands to create database in dump
-e, --extension=PATTERN               # dump the specified extension(s) only
-E, --encoding=ENCODING               # dump the data in encoding ENCODING
-n, --schema=PATTERN                  # dump the specified schema(s) only
-N, --exclude-schema=PATTERN          # do NOT dump the specified schema(s)
-O, --no-owner                        # skip restoration of object ownership in plain-text format
-s, --schema-only                     # dump only the schema, no data
-S, --superuser=NAME                  # superuser user name to use in plain-text format
-t, --table=PATTERN                   # dump the specified table(s) only
-T, --exclude-table=PATTERN           # do NOT dump the specified table(s)
-x, --no-privileges                   # do not dump privileges (grant/revoke)
    --binary-upgrade                  # for use by upgrade utilities only
    --column-inserts                  # dump data as INSERT commands with column names
    --disable-dollar-quoting          # disable dollar quoting, use SQL standard quoting
    --disable-triggers                # disable triggers during data-only restore
    --enable-row-security             # enable row security (dump only content user has access to)
    --exclude-table-data=PATTERN      # do NOT dump data for the specified table(s)
    --extra-float-digits=NUM          # override default setting for extra_float_digits
    --if-exists                       # use IF EXISTS when dropping objects
    --include-foreign-data=PATTERN    # include data of foreign tables on foreign servers matching PATTERN
    --inserts                         # dump data as INSERT commands, rather than COPY
    --load-via-partition-root         # load partitions via the root table
    --no-comments                     # do not dump comments
    --no-publications                 # do not dump publications
    --no-security-labels              # do not dump security label assignments
    --no-subscriptions                # do not dump subscriptions
    --no-synchronized-snapshots       # do not use synchronized snapshots in parallel jobs
    --no-tablespaces                  # do not dump tablespace assignments
    --no-toast-compression            # do not dump TOAST compression methods
    --no-unlogged-table-data          # do not dump unlogged table data
    --on-conflict-do-nothing          # add ON CONFLICT DO NOTHING to INSERT commands
    --quote-all-identifiers           # quote all identifiers, even if not key words
    --rows-per-insert=NROWS           # number of rows per INSERT; implies --inserts
    --section=SECTION                 # dump named section (pre-data, data, or post-data)
    --serializable-deferrable         # wait until the dump can run without anomalies
    --snapshot=SNAPSHOT               # use given snapshot for the dump
    --strict-names                    # require table and/or schema include patterns to match at least one entity each
    --use-set-session-authorization   # use SET SESSION AUTHORIZATION commands instead of ALTER OWNER commands to set ownership

# connection options
-d, --dbname=DBNAME         # database to dump, If no database name is supplied, then the PGDATABASE variable value is used
-h, --host=HOSTNAME         # database server host or socket directory
-p, --port=PORT             # database server port number
-U, --username=NAME         # connect as specified database user
-w, --no-password           # never prompt for password
-W, --password              # force password prompt (should happen automatically)
    --role=ROLENAME         # do SET ROLE before dump
```

## usage

```sh
pg_dump -h HOST -p PORT -U USER -d DATABASE > FILE.dump

pg_dump DATABASE > db.sql                               # dump database called DATABASE into sql-script file

pg_dump --host localhost --port 5432 --username "userName" --schema-only --verbose --file "file path" "db_dev_local"

psql -d NEWDB -f db.sql                                 # reload script into a (freshly created) database: NEWDB

pg_dump -Fc DATABASE > db.dump                          # dump database into custom-format archive file
pg_dump -Fd DATABASE -f dumpdir                         # dump database into directory-format archive
pg_dump -Fd DATABASE -j 5 -f dumpdir                    # dump database into directory-format archive in parallel with 5 worker jobs

pg_restore -d NEWDB db.dump                             # reload an archive file into a (freshly created) database: NEWDB

pg_dump -t TABLE DATABASE > db.sql                      # dump a single table
pg_dump -t "\"MixedCaseName\"" DATABASE > mytab.sql     # specify upper-/mixed-case name in -t and related switches, name needs to be double-quoted else it will be folded to lower case (see Patterns)

pg_dump -t 'detroit.emp*' -T detroit.employee_log DATABASE > db.sql   # dump all tables whose names start with emp in the detroit schema, except for the table named employee_log
pg_dump -n 'east*gsm' -n 'west*gsm' -N '*test*' DATABASE > db.sql     # dump all schemas whose names start with east or west and end in gsm, excluding schemas whose names contain word test
pg_dump -n '(east|west)*gsm' -N '*test*' DATABASE > db.sql            # same as above, using regular expression notation to consolidate the switches
pg_dump -T 'ts_*' DATABASE > db.sql                                   # dump all database objects except for tables whose names begin with ts_
```

```sh
-F  # custom format for pg_restore
-O  # do not output ownership commands (important: prevents objects from being restored with old roles/owners)
-x  # do not dump privileges (grants), making it cleaner to reassign later
pg_restore -h host_bar -U bar_role -d bar -n public foo.dump

pg_restore -h host_bar -U bar_role -d bar -n public foo.dump
```

## see also

- [[pg_restore]]
- [[pg_dumpall]]
- [[pg_activity]]
- [[psql]]
- [[mysqldump]]
- [[mongodump]]
- [postgresql.org/docs/9.0/libpq-envars](https://www.postgresql.org/docs/9.0/libpq-envars.html)

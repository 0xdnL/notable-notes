---
tags: [database/postgresql, linux]
title: psql
created: '2019-07-30T06:19:49.220Z'
modified: '2024-06-17T09:53:42.564Z'
---

# psql

> postgresql - object-relational database management system written in [[c]]

## install

```sh
apt install postgresql
apk add postgresql-client

brew install postgresql@14
brew services start postgresql@14                                                       # start postgresql@14 service
$HOMEBREW_PREFIX/opt/postgresql@14/bin/postgres -D $HOMEBREW_PREFIX/var/postgresql@14   # start background service directly

docker run -ti --rm -e POSTGRES_PASSWORD=password postgres psql -U postgres

pgenv build 15.0 && pgenv use 15.0
```

## .psqlrc

```sh
# -- \set PROMPT1 '(%n@%M:%>) %`date +%H:%M:%S` [%/] \n%x%# '
# -- \set PROMPT1 '%[%033[1;31;40m%]%/%R%[%033[0m%]%# '

cat <<EOF > ~/.psqlrc
\set PROMPT1 '(%n@%M:%>) [%/]%x%# '
\set ON_ERROR_ROLLBACK interactive
\set COMP_KEYWORD_CASE upper
\set HISTFILE ~/.psql/history- :DBNAME
\pset pager off
\pset null '(null)' 
EOF
```

[wiki.postgresql.org/wiki/Psqlrc](https://wiki.postgresql.org/wiki/Psqlrc)

## environment

```sh
PGHOST                    # behaves the same as the host connection parameter
PGHOSTADDR                # behaves the same as the hostaddr connection parameter. This can be set instead of or in addition to PGHOST to avoid DNS lookup overhead
PGPORT                    # behaves the same as the port connection parameter
PGDATABASE                # behaves the same as the dbname connection parameter
PGUSER                    # behaves the same as the user connection parameter
PGPASSWORD                # behaves the same as the password connection parameter
PGPASSFILE                # behaves the same as the passfile connection parameter
PGREQUIREAUTH             # behaves the same as the require_auth connection parameter
PGCHANNELBINDING          # behaves the same as the channel_binding connection parameter
PGSERVICE                 # behaves the same as the service connection parameter
PGSERVICEFILE             # specifies the name of the per-user connection service file (see Section 34.17). Defaults to ~/.pg_service.conf
PGOPTIONS                         # behaves the same as the options connection parameter
PGOPTIONS='--search_path=myschma' # set schema
PGAPPNAME                 # behaves the same as the application_name connection parameter
PGSSLMODE                 # behaves the same as the sslmode connection parameter
PGREQUIRESSL              # behaves the same as the requiressl connection parameter. deprecated in favor of the PGSSLMOD
PGSSLCOMPRESSION          # behaves the same as the sslcompression connection parameter
PGSSLCERT                 # behaves the same as the sslcert connection parameter
PGSSLKEY                  # behaves the same as the sslkey connection parameter
PGSSLCERTMODE             # behaves the same as the sslcertmode connection parameter
PGSSLROOTCERT             # behaves the same as the sslrootcert connection parameter
PGSSLCRL                  # behaves the same as the sslcrl connection parameter
PGSSLCRLDIR               # behaves the same as the sslcrldir connection parameter
PGSSLSNI                  # behaves the same as the sslsni connection parameter
PGREQUIREPEER             # behaves the same as the requirepeer connection parameter
PGSSLMINPROTOCOLVERSION   # behaves the same as the ssl_min_protocol_version connection parameter
PGSSLMAXPROTOCOLVERSION   # behaves the same as the ssl_max_protocol_version connection parameter
PGGSSENCMODE              # behaves the same as the gssencmode connection parameter
PGKRBSRVNAME              # behaves the same as the krbsrvname connection parameter
PGGSSLIB                  # behaves the same as the gsslib connection parameter
PGGSSDELEGATION           # behaves the same as the gssdelegation connection parameter
PGCONNECT_TIMEOUT         # behaves the same as the connect_timeout connection parameter
PGCLIENTENCODING          # behaves the same as the client_encoding connection parameter
PGTARGETSESSIONATTRS      # behaves the same as the target_session_attrs connection parameter
PGLOADBALANCEHOSTS        # behaves the same as the load_balance_hosts connection parameter
# specify default behavior for each PostgreSQL session
PGDATESTYLE   # sets the default style of date/time representation. (Equivalent to SET datestyle TO ....)
PGTZ          # sets the default time zone. (Equivalent to SET timezone TO ....)
PGGEQO        # sets the default mode for the genetic query optimizer. (Equivalent to SET geqo TO ....)
# determine internal behavior of libpq; they override compiled-in defaults
PGSYSCONFDIR  # sets the directory containing the pg_service.conf file and in a future version possibly other system-wide configuration files
PGLOCALEDIR   # sets the directory containing the locale files for message localization


LANG=C psql.
```

[postgresql.org/docs/current/libpq-envars](https://www.postgresql.org/docs/current/libpq-envars.html)

## option

```sh
# General options
-c, --command=COMMAND               # run only single command (SQL or internal) and exit
-d, --dbname=DBNAME                 # database name to connect to (default: "daniel")
-f, --file=FILENAME                 # execute commands from file, then exit
-l, --list                          # list available databases, then exit
-v, --set=, --variable=NAME=VALUE   # set psql variable NAME to VALUE (e.g., -v ON_ERROR_STOP=1)
-V, --version                       # output version information, then exit
-X, --no-psqlrc                     # do not read startup file (~/.psqlrc)
-1 ("one"), --single-transaction    # execute as a single transaction (if non-interactive)
-?, --help[=options]                # show this help, then exit
    --help=commands                 # list backslash commands, then exit
    --help=variables                # list special variables, then exit

# Input and output options
-a, --echo-all            # echo all input from script
-b, --echo-errors         # echo failed commands
-e, --echo-queries        # echo commands sent to server
-E, --echo-hidden         # display queries that internal commands generate
-L, --log-file=FILENAME   # send session log to file
-n, --no-readline         # disable enhanced command line editing (readline)
-o, --output=FILENAME     # send query results to file (or |pipe)
-q, --quiet               # run quietly (no messages, only query output)
-s, --single-step         # single-step mode (confirm each query)
-S, --single-line         # single-line mode (end of line terminates SQL command)

# Output format options
-A, --no-align                  # unaligned table output mode
    --csv                       # CSV (Comma-Separated Values) table output mode
-F, --field-separator=STRING    # field separator for unaligned output (default: "|")
-H, --html                      # HTML table output mode
-P, --pset=VAR[=ARG]            # set printing option VAR to ARG (see \pset command)
-R, --record-separator=STRING   # record separator for unaligned output (default: newline)
-t, --tuples-only               # print rows only
-T, --table-attr=TEXT           # set HTML table tag attributes (e.g., width, border)
-x, --expanded                  # turn on expanded table output
-z, --field-separator-zero      # set field separator for unaligned output to zero byte
-0, --record-separator-zero     # set record separator for unaligned output to zero byte

# connection options
-h, --host=HOSTNAME      # database server host or socket directory (default: "local socket")
-p, --port=PORT          # database server port (default: "5432")
-U, --username=USERNAME  # database user name (default: "daniel")
-w, --no-password        # never prompt for password
-W, --password           # force password prompt (should happen automatically)
```

## usage

```sh
psql -E                                                     # show sql-query equivalent of interal command

psql -U postgres -d DATABASE                                # connect to DATABASE

psql -U postgres -h HOST -p 5432 -tAc "SELECT 1"            # can be used to check if database is available after deployment

psql -U postgres -d DATABASE -c "SELECT * FROM some_table"  # run query
```

## internal commands / meta commands

```sql
\? [commands]           -- show help on backslash commands
\? options              -- show help on psql command-line options
\? variables            -- show help on special variables

\h [NAME]               -- help on syntax of SQL commands, * for all commands
\h CREATE ROLE


\copyright              -- show PostgreSQL usage and distribution terms
\crosstabview [COLUMNS] -- execute query and display results in crosstab
\errverbose             -- show most recent error message at maximum verbosity
\g [(OPTIONS)] [FILE]   -- execute query (and send results to file or |pipe); \g with no arguments is equivalent to a semicolon
\gdesc                  -- describe result of query, without executing it
\gexec                  -- execute query, then execute each value in its result
\gset [PREFIX]          -- execute query and store results in psql variables
\gx [(OPTIONS)] [FILE]  -- as \g, but forces expanded output mode
\q                      -- quit psql
\watch [SEC]            -- execute query every SEC seconds

-- Query Buffer
\e [FILE] [LINE]        -- edit the query buffer (or file) with external editor
\ef [FUNCNAME [LINE]]   -- edit function definition with external editor
\ev [VIEWNAME [LINE]]   -- edit view definition with external editor
\p                      -- show the contents of the query buffer
\r                      -- reset (clear) the query buffer
\s [FILE]               -- display history or save it to file
\w FILE                 -- write query buffer to file

-- Input/Output
\copy ...               -- perform SQL COPY with data stream to the client host

\echo [-n] [STRING]     -- write string to standard output (-n for no newline)
\echo :DBNAME :PORT :USER   -- print some preset variables

\i FILE                 -- execute commands from file
\ir FILE                -- as \i, but relative to location of current script
\o [FILE]               -- send all query results to file or |pipe
\qecho [-n] [STRING]    -- write string to \o output stream (-n for no newline)
\warn [-n] [STRING]     -- write string to standard error (-n for no newline)

-- Conditional
\if EXPR                -- begin conditional block
\elif EXPR              -- alternative within current conditional block
\else                   -- final alternative within current conditional block
\endif                  -- end conditional block

-- Informational  (options: S = show system objects, + = additional detail)
\dt               -- list all tables in current database
\dn               -- list all schema in current database
\d+ table         -- describe

\d[S+]                        -- list tables, views, and sequences
\d[S+]  NAME                  -- describe table, view, sequence, or index
\da[S]  [PATTERN]             -- list aggregates
\dA[+]  [PATTERN]             -- list access methods
\dAc[+] [AMPTRN TYPEPTRN]     -- list operator classes
\dAf[+] [AMPTRN TYPEPTRN]     -- list operator families
\dAo[+] [AMPTRN OPFPTRN]      -- list operators of operator families
\dAp[+] [AMPTRN OPFPTRN]      -- list support functions of operator families
\db[+]  [PATTERN]             -- list tablespaces
\dc[S+] [PATTERN]             -- list conversions
\dC[+]  [PATTERN]             -- list casts
\dd[S]  [PATTERN]             -- show object descriptions not displayed elsewhere
\dD[S+] [PATTERN]             -- list domains
\ddp    [PATTERN]             -- list default privileges
\dE[S+] [PATTERN]             -- list foreign tables
\des[+] [PATTERN]             -- list foreign servers
\det[+] [PATTERN]             -- list foreign tables
\deu[+] [PATTERN]             -- list user mappings
\dew[+] [PATTERN]             -- list foreign-data wrappers
\df[anptw][S+] [FUNCPTRN [TYPEPTRN...] -- list [only agg/normal/procedure/trigger/window] functions
\dF[+]  [PATTERN]             -- list text search configurations
\dFd[+] [PATTERN]             -- list text search dictionaries
\dFp[+] [PATTERN]             -- list text search parsers
\dFt[+] [PATTERN]             -- list text search templates
\dg[S+] [PATTERN]             -- list roles
\di[S+] [PATTERN]             -- list indexes
\dl                           -- list large objects, same as \lo_list
\dL[S+] [PATTERN]             -- list procedural languages
\dm[S+] [PATTERN]             -- list materialized views
\dn[S+] [PATTERN]             -- list schemas
\do[S+] [OPPTRN TYPEPTRN TYPEPTRN]    -- list operators
\dO[S+] [PATTERN]             -- list collations
\dp     [PATTERN]             -- list table, view, and sequence access privileges
\dP[itn+] [PATTERN]           -- list [only index/table] partitioned relations [n=nested]
\drds [ROLEPTRN DBPTRN]       -- list per-database role settings
\dRp[+] [PATTERN]             -- list replication publications
\dRs[+] [PATTERN]             -- list replication subscriptions
\ds[S+] [PATTERN]             -- list sequences
\dt[S+] [PATTERN]             -- list tables
\dT[S+] [PATTERN]             -- list data types
\du[S+] [PATTERN]             -- list roles
\dv[S+] [PATTERN]             -- list views
\dx[+]  [PATTERN]             -- list extensions
\dX     [PATTERN]             -- list extended statistics
\dy[+]  [PATTERN]             -- list event triggers
\l[+]   [PATTERN]             -- list databases
\sf[+]  FUNCNAME              -- show a function's definition
\sv[+]  VIEWNAME              -- show a view's definition
\z      [PATTERN]             -- same as \dp

-- Formatting
\a                     -- toggle between unaligned and aligned output mode
\C [STRING]            -- set table title, or unset if none
\f [STRING]            -- show or set field separator for unaligned query output
\H                     -- toggle HTML output mode
\pset [NAME VALUE]     -- set table output option (border|columns|csv_fieldsep|..)
\t [on|off]            -- show only rows
\T [STRING]            -- set HTML <table> tag attributes, or unset if none
\x [on|off|auto]       -- toggle expanded output

-- Connection
\c[onnect] {[DBNAME|- USER|- HOST|- PORT|-] | conninfo} -- connect to new database
\connect DBNAME        -- connect to database
\c postgres postgres   -- connect to database postgres as role postgres

\conninfo              -- display information about current connection
\encoding [ENCODING]   -- show or set client encoding
\password [USERNAME]   -- securely change the password for a user

-- Operating System
\cd [DIR]              -- change the current working directory
\setenv NAME [VALUE]   -- set or unset environment variable
\timing [on|off]       -- toggle timing of commands
\! [COMMAND]           -- execute command in shell or start interactive shell

-- Variables
\prompt [TEXT] NAME     -- prompt user to set internal variable
\echo :NAME             -- print prompted value later

\set [NAME VALUE]       -- set internal variable, or list all if no parameters
\SET search_path TO SCHEMA_NAME;

\unset NAME             -- unset (delete) internal variable
```

## sql

```sql
SELECT current_database();  -- get currently connected db           \conninfo
SELECT current_schema();    -- get currently schema e.g. "public"   \dn
SELECT current_user;

SELECT current_user, current_database(), current_schema();

SELECT n.nspname AS schema_name
FROM pg_namespace n
WHERE has_schema_privilege('postgres',n.nspname, 'CREATE, USAGE');


SELECT table_name FROM information_schema.tables WHERE table_schema = 'public';

SELECT version();                           -- get server version
SELECT current_setting('LC_MESSAGES');      -- locale..

SELECT pg_size_pretty( pg_database_size('DATABASE') );    -- get db size


SHOW hba_file;            -- show host-based-access conf file
SHOW data_directory;      -- show log file
DESCRIBE TABLE
```

## roles and priviliges

```sql
SELECT * FROM pg_user;    -- list all roles/users
SELECT * FROM pg_roles;

-- shows which user has which grant on table mytable
SELECT grantee, privilege_type FROM information_schema.role_table_grants WHERE table_name='mytable';

SELECT EXISTS (SELECT 1 FROM information_schema.tables WHERE table_name = 'name_of_table') AS table_existence;

CREATE ROLE user_name WITH LOGIN PASSWORD 'secret_passwd';
CREATE USER user_name WITH LOGIN PASSWORD 'secret_passwd';

ALTER ROLE user_name WITH PASSWORD 'secret_passwd';
ALTER USER user_name WITH PASSWORD 'secret_passwd';


-- init
CREATE DATABASE bookstore;
CREATE USER bookstore_user WITH ENCRYPTED PASSWORD 'secret';
GRANT ALL PRIVILEGES ON DATABASE bookstore TO bookstore_user;
GRANT ALL PRIVILEGES ON TABLE books TO bookstore_user;
```

## transactions

```sql
BEGIN;  -- "dryrun" a transaction
  UPDATE users SET admin = 't' WHERE id = '38'; 
  select admin from users where id = '38'; 
ROLLBACK; 
```

## DO block

```sql
DO $$
DECLARE r record;
BEGIN
  FOR r IN 
    SELECT table_schema, table_name 
    FROM information_schema.tables
    WHERE table_type = 'VIEW' AND table_schema = 'public'
  LOOP
      EXECUTE 'GRANT ALL ON ' || quote_ident(r.table_schema) || '.' || quote_ident(r.table_name) || ' TO webuser';
  END LOOP;
END$$;

DO $$
BEGIN 
  IF NOT EXISTS (SELECT FROM pg_roles WHERE rolname = 'prometheus_exporter') THEN 
    CREATE ROLE prometheus_exporter LOGIN PASSWORD '${PASSWORD}'; 
  ELSE 
    ALTER USER prometheus_exporter WITH PASSWORD '${PASSWORD}'; 
  END IF; 
  
  GRANT pg_monitor to prometheus_exporter; 
  GRANT CONNECT ON DATABASE postgres TO prometheus_exporter; 
END $$;

DO $$
DECLARE
    db_name TEXT;
    role_name TEXT;
BEGIN
    FOR db_name IN ARRAY['db_a', 'db_b', 'db_c']
    LOOP
        role_name := 'developer' || db_name || 'ReadOnlyRole';
        EXECUTE 'CREATE ROLE ' || role_name;
        EXECUTE 'GRANT CONNECT, CREATE, USAGE ON DATABASE ' || db_name || ' TO ' || role_name;
        EXECUTE 'GRANT SELECT, INSERT, UPDATE, DELETE ON ALL TABLES IN SCHEMA public TO ' || role_name;
    END LOOP;
END $$;



DO $$
DECLARE
    db_name TEXT;
    role_name TEXT;
    db_cursor CURSOR FOR SELECT unnest(ARRAY['db_a', 'db_b', 'db_c']);
BEGIN
    OPEN db_cursor;
    LOOP
        FETCH db_cursor INTO db_name;
        EXIT WHEN NOT FOUND;

        role_name := 'developer8_' || db_name || '_ReadOnlyRole';
        EXECUTE 'CREATE ROLE ' || role_name || ' LOGIN PASSWORD "your_password"';
        EXECUTE 'GRANT CONNECT ON DATABASE ' || db_name || ' TO ' || role_name;
        EXECUTE 'GRANT SELECT ON ALL TABLES IN SCHEMA public TO ' || role_name;
        EXECUTE 'ALTER ROLE ' || role_name || ' WITH PASSWORD ''your_password''';
    END LOOP;

    CLOSE db_cursor;
END $$;
```

## see also

- [[pgenv]]
- [[pg_dump]], [[pg_dumpall]]
- [[mysql]], [[sqlite]]
- [[mongo]]
- [postgresql.org/docs/current](https://www.postgresql.org/docs/current/index.html)
- [PSQL-META-COMMANDS](https://www.postgresql.org/docs/current/static/app-psql.html#APP-PSQL-META-COMMANDS)
- [alternate-output-format-for-psql](https://stackoverflow.com/questions/9604723/alternate-output-format-for-psql)


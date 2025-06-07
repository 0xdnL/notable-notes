---
title: patronictl
created: '2025-02-18T11:26:13.896Z'
modified: '2025-02-26T14:03:25.591Z'
---

# patronictl

> cli for interacting with patroni REST API and with the dyn config settings ([[etcd]])

## usage

```sh
-c, --config-file TEXT     # Configuration file
-d, --dcs-url, --dcs TEXT  # The DCS connect url
-k, --insecure             # Allow connections to SSL sites without certs
    --help                 # Show this message and exit
```

## commands

```sh
patronictl list           # List the Patroni members for a given Patroni
patronictl history        # Show the history of failovers/switchovers

patronictl dsn            # Generate a dsn for the provided member, defaults to a dsn...
patronictl edit-config    # Edit cluster configuration
patronictl failover       # Failover to a replica
patronictl flush          # Discard scheduled events

patronictl pause          # Disable auto failover
patronictl query          # Query a Patroni PostgreSQL member
patronictl reinit         # Reinitialize cluster member
patronictl reload         # Reload cluster member configuration
patronictl remove         # Remove cluster from DCS
patronictl restart        # Restart cluster member
patronictl resume         # Resume auto failover
patronictl show-config    # Show cluster configuration
patronictl switchover     # Switchover to a replica
patronictl topology       # Prints ASCII topology for given cluster
patronictl version        # Output version of patronictl command or a running Patroni...
```

## postgresql

```sql
select * from pg_stat_replication;    -- find out state, sync-state etc
```

## see also

- [[psql]]
- [patroni.readthedocs.io/en/latest/patronictl](https://patroni.readthedocs.io/en/latest/patronictl.html)

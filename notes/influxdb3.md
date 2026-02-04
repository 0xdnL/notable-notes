---
title: influxdb3
created: '2026-01-22T13:59:35.536Z'
modified: '2026-01-23T09:33:19.917Z'
---

# influxdb3

> db built to collect, process, transform and store event and time series data

## install

```sh
docker run -it -p 8181:8181\
  influxdb:3-core \
  influxdb3 serve \
  --node-id node0 \
  --object-store file \
  --data-dir=/var/lib/influxdb3/data
  --plugin-dir=/var/lib/influxdb3/plugins
```

[[docker]]


## environment

```sh
INFLUXDB3_AUTH_TOKEN
```

## Common Commands

```sh
influxdb3 serve     # Run the InfluxDB 3 Core server
influxdb3 serve --node-id node0 --object-store file --data-dir ~/.influxdb3_data

influxdb3 query, q  # Perform a query against a running InfluxDB 3 Core server
influxdb3 query -d home 'select * from home order by time'

influxdb3 write, w  # Perform a set of writes to a running InfluxDB 3 Core server
influxdb3 write --database DATABASE_NAME --token AUTH_TOKEN --precision s \
'home,room=Living\ Room temp=21.1,hum=35.9,co=0i 1641024000
home,room=Kitchen temp=21.0,hum=35.9,co=0i 1641024000'

influxdb3 update    # Update resources on the InfluxDB 3 Core server
```

## Resource Management

```sh
influxdb3 create    # Create a resource such as a database or auth token
influxdb3 create token --admin


influxdb3 show      # List resources on the InfluxDB 3 Core server
influxdb3 show tokens --token $TOKEN

influxdb3 delete    # Delete a resource such as a database or table
influxdb3 enable    # Enable a resource such as a trigger
influxdb3 disable   # Disable a resource such as a trigger
```

## System Management

```sh
influxdb3 install   # Install Python packages for the Processing Engine
influxdb3 test      # Test that Processing Engine plugins work the way you expect
```

## see also

- [[prometheus]]

---
tags: [go, linux]
title: logcli
created: '2024-04-04T11:04:46.625Z'
modified: '2024-12-05T08:39:07.096Z'
---

# logcli

> cli for loki

[grafana.com/docs/loki/latest/query/logcli](https://grafana.com/docs/loki/latest/query/logcli/)

## install

```sh
git clone https://github.com/grafana/loki.git && cd loki
make logcli
cp ./cmd/logcli/logcli $HOME/go/bin
```

## environment

```sh
LOKI_ADDR       # https://logs-us-west1.grafana.net
LOKI_USERNAME   # If you are running on Grafana Cloud
LOKI_PASSWORD   # If you are running on Grafana Cloud

LOKI_ORG_ID
LOKI_QUERY_TAGS
LOKI_HTTP_PROXY_URL
LOKI_HTTP_COMPRESSION

LOKI_CLIENT_RETRIES
LOKI_CLIENT_MIN_BACKOFF
LOKI_CLIENT_MAX_BACKOFF
LOKI_AUTH_HEADER
LOKI_HTTP_PROXY_URL
LOKI_HTTP_COMPRESSION
```

## option

```sh

```

## series

```sh
logcli series '{}' --analyze-labels

LOKI_ADDR=http://localhost:51645 logcli series '{}' --analyze-labels
```

## query

> run a LogQL query

```sh
    --stats                         # show query statistics
-o, --output=default                # output mode: [default|raw|jsonl]
                                    #   raw       : log line, suppresses log labels and timestamp
                                    #   default   : log timestamp + log labels + log line
                                    #   jsonl     : json response from Loki API of log line
-z, --timezone=Local                # specify the timezone to use when formatting output timestamps [Local, UTC]
    --stdin                         # take input logs from stdin
    --addr="http://localhost:3100"  # server address, LOKI_ADDR

    --since=1h                      # lookback window
    --from=FROM                     # start looking for logs at this absolute time (inclusive) ensure to use RFC3339Nano time format
    --to=TO                         # stop looking for logs at this absolute time (exclusive)  ensure to use RFC3339Nano time format
    --step=STEP                     # query resolution step width, for metric queries. Evaluate the query at the specified step over the time range.
    --interval=INTERVAL             # query interval, for log queries. Return entries at the specified interval, ignoring those between. EXPERIMENTAL
```

```sh
logcli query --timezone=UTC --from="2024-11-26T00:00:00Z" --to="2024-11-27T23:59:00Z" --output=jsonl \
  '{app="postgres-cluster",container="postgres",namespace="default"} |~ "ALTER USER .* WITH PASSWORD"'

logcli query '{job="loki-ops/consul"}'

logcli query '{app="postgres-cluster",container="postgres",namespace="default"}'

cat mylog.log | logcli --stdin query '|="too many open connections"'
cat mylog.log | logcli --stdin query '| pattern <ip> - - <_> "<method> <uri> <_>" <status> <size> <_> "<agent>" <_>'
cat mylog.log | logcli --stdin query '| logfmt | line_format "{{.query}} {{.duration}}"'

echo 'msg="timeout happened" level="warning"' | logcli --stdin query '|logfmt|level="warning"'
```

```sh
curl -G -s  "http://localhost:3100/loki/api/v1/query" \
  --data-urlencode 'query=sum(rate({job="varlogs"}[10m])) by (level)' | jq

curl -G -s  "http://localhost:3100/loki/api/v1/query" \
  --data-urlencode 'query={app="postgres-cluster",container="postgres",namespace="default"}'
```

## queries

```sh
'{foo="bar",baz=~".*blip"} |~ ".*error.*"'

{app="kube-api",source="event-exporter"} | json | reason="Killing" | line_format "{{ .message }}"


{app="postgres-cluster",container="postgres",namespace="default"} |= "ALTER USER" |~ "WITH PASSWORD" 
{app="postgres-cluster",container="postgres",namespace="default"} |~ "ALTER USER .* WITH PASSWORD"
{app="postgres-cluster",container="postgres",namespace="default"} |~ "ALTER USER [^ ]+ WITH PASSWORD"
```

[grafana.com/docs/loki/latest/query/query_examples](https://grafana.com/docs/loki/latest/query/query_examples/)

## see also

- [[promtool]]
- [[curl]]

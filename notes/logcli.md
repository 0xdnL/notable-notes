---
title: logcli
created: '2024-04-04T11:04:46.625Z'
modified: '2024-06-06T08:32:51.867Z'
---

# logcli

> cli for loki

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
```

## option

```sh

```

## usage

```sh
logcli series '{}' --analyze-labels


LOKI_ADDR=http://localhost:51645 logcli series '{}' --analyze-labels

{app="kube-api",source="event-exporter"} | json | reason="Killing" | line_format "{{ .message }}"
```

## see also

- [[promtool]]

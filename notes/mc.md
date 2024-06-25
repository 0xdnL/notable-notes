---
tags: [cloud, go, linux]
title: mc
created: '2019-09-19T12:03:17.162Z'
modified: '2024-04-02T09:51:49.074Z'
---

# mc

> minio client for cloud storage and filesystems

## install

```sh
GO111MODULE=on go get github.com/minio/mc

curl -O https://dl.min.io/client/mc/release/linux-amd64/mc

brew install minio/stable/minio

minio --autocompletion              # install auto-completion
```

## environment

```sh
MC_QUIET
MC_NO_COLOR
MC_JSON
MC_DEBUG
MC_INSECURE
MC_LIMIT_UPLOAD

MC_HOST_<ALIAS>         # Replace <ALIAS> at the end of the environment variable with the alias to set the host for
MC_STS_ENDPOINT_<ALIAS> # add an STS endpoint
```

## options

```sh
          --autocompletion              # install auto-completion for your shell
-C VALUE, --config-dir VALUE            # path to configuration folder (default: "$HOME/.mc") [$MC_CONFIG_DIR]
-q,       --quiet                       # disable progress bar display [$MC_QUIET]
          --no-color                    # disable color theme [$MC_NO_COLOR]
          --json                        # enable JSON lines formatted output [$MC_JSON]
          --debug                       # enable debug output [$MC_DEBUG]
          --insecure                    # disable SSL certificate verification [$MC_INSECURE]
          --limit-upload VALUE          # limits uploads to a maximum rate in KiB/s, MiB/s, GiB/s. (default: unlimited) [$MC_LIMIT_UPLOAD]
          --limit-download VALUE        # limits downloads to a maximum rate in KiB/s, MiB/s, GiB/s. (default: unlimited) [$MC_LIMIT_DOWNLOAD]
-h,       --help                        # show help
-v,       --version                     # print the version
```

## config (deprecated)

```sh
mc config host list

mc config host add minio http://127.0.0.1:9000 KEYID SECRETKEY
```

## alias

> manage server credentials in configuration file

```sh
bash +o history
mc alias set ALIAS HOSTNAME ACCESS_KEY SECRET_KEY
bash -o history
```

## admin

> manage MinIO servers

```sh
```

## anonymous

> manage anonymous access to buckets and objects

```sh
```

## batch

> manage batch jobs

```sh
```

## cp

> copy objects

```sh
```

## cat

> display object contents

```sh
```

## diff

> list differences in object name, size, and date between two buckets

```sh
```

## du

> summarize disk usage recursively

```sh
```

## encrypt

> manage bucket encryption config

```sh
```

## event

> manage object notifications

```sh
```

## find

> search for objects

```sh
```

## get

> get s3 object to local

```sh
```

## head

> display first 'n' lines of an object

```sh
```

## ilm

> manage bucket lifecycle

```sh
```

## idp

> manage MinIO IDentity Provider server configuration

```sh
```

## license

> license related commands

```sh
```

## legalhold

> manage legal hold for object(s)

```sh
```

## ls

> list buckets and objects

```sh
mc ls BUCKET
```

## mb

> make a bucket

```sh
```

## mv

> move objects

```sh
```

## mirror

> synchronize object(s) to a remote site

```sh
mc mirror PATH BUCKET
```

## od

> measure single stream upload and download

```sh
```

## ping

> perform liveness check

```sh
```

## pipe

> stream STDIN to an object

```sh
```

## put

> upload an object to a bucket

```sh
```

## quota

> manage bucket quota

```sh
```

## rm

> remove object(s)

```sh
```

## retention

> set retention for object(s)

```sh
```

## rb

> remove a bucket

```sh
```

## replicate

> configure server side bucket replication

```sh
```

## ready

> checks if the cluster is ready or not

```sh
```

## sql

> run sql queries on objects

```sh
```

## stat

> show object metadata

```sh
```

## support

> support related commands

```sh
```

## share

> generate URL for temporary access to an object

```sh
```

## tree

> list buckets and objects in a tree format

```sh
```

## tag

> manage tags for bucket and object(s)

```sh
```

## undo

> undo PUT/DELETE operations

```sh
```

## update

> update mc to latest release

```sh
```

## version

> manage bucket versioning

```sh
```

## watch

> listen for object notification events

```sh
```

## see also

- [[aws]] `s3`, `s3api`
- [[govc]]
- [[jq]], [[yq]]
- [[helm]]
- [[rsync]]
- [[bash]]

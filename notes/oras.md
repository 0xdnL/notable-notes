---
title: oras
created: '2025-12-08T13:20:16.783Z'
modified: '2025-12-08T13:38:35.875Z'
---

# oras

> provides a way to push and pull OCI Artifacts to and from OCI Registries (`"Open Container Initiative"`)

[[helm]] [[docker]] [[crane]] [[skopeo]] [[crictl]]

## install

```sh
VERSION="1.3.0"
curl -LO "https://github.com/oras-project/oras/releases/download/v${VERSION}/oras_${VERSION}_darwin_arm64.tar.gz"
mkdir -p oras-install/
tar -zxf oras_${VERSION}_*.tar.gz -C oras-install/
sudo mv oras-install/oras /usr/local/bin/
rm -rf oras_${VERSION}_*.tar.gz oras-install/
```

https://oras.land/docs/installation

## usage

```sh
docker login              # auth
~/.docker/config.json     # auth

oras repo tags ghcr.io/prometheus-community/charts/prometheus-postgres-exporter

oras manifest fetch --pretty ghcr.io/prometheus-community/charts/prometheus-postgres-exporter:5.1.0
```

## see also

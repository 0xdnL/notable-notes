---
tags: [container]
title: pluto
created: '2024-09-03T12:22:17.418Z'
modified: '2024-10-08T09:23:08.343Z'
---

# pluto

> utility to help users find deprecated Kubernetes apiVersions in code repositories and helm releases


## install

```sh
asdf plugin-add pluto
asdf list-all pluto
asdf install pluto <latest version>
asdf local pluto <latest version>
```

[[asdf]]

## usage

```sh
pluto detect-files -d pkg/finder/testdata

pluto detect-helm -owide
pluto detect-helm -n cert-manager -owide

helm template e2e/tests/assets/helm3chart | pluto detect -

pluto detect-api-resources -owide

pluto detect-all-in-cluster -o wide 2>/dev/null  # helm and API resources in cluster
```

## see also

- [[kubectl]]
- [[helm]]


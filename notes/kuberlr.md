---
title: kuberlr
created: '2024-11-16T05:14:52.146Z'
modified: '2025-05-05T12:04:26.714Z'
---

# kuberlr

> "`kube-ruler`" - simple wrapper for [[kubectl]] which makes it easy to manage clusters running different versions of kubernetes

## install

comes bundled with [[rdctl]] or:

```sh
curl -LO https://github.com/flavio/kuberlr/releases/download/v0.6.0/kuberlr_0.6.0_darwin_arm64.tar.gz
cp kuberlr /bin/
ln -s ~/bin/kuberlr ~/bin/kubectl
```

## usage

```sh
kuberlr bins              # print information about the kubectl binaries found

kuberlr completion        # Generate the autocompletion script for the specified shell

kuberlr get               # Download the kubectl version specified

kuberlr help              # Help about any command

kuberlr kubectl           # Wrap and exec a suitable version kubectl command

kuberlr version           # Print version information
```

## see also

- [[kubectl]]
- [[kubie]], [[kubectx]]
- [github.com/flavio/kuberlr](https://github.com/flavio/kuberlr)

---
tags: [container]
title: helmfile
created: '2024-06-21T08:35:29.414Z'
modified: '2024-10-08T09:22:15.740Z'
---

# helmfile

> declarative spec for deploying helm charts

## install

> needs [[helm]] and plugins `helm diff`, `helm secrets`, `helm helm-git`, `helm s3` which can be installed via init

```sh
brew install helmfile

helmfile completion  # generate the autocompletion script for the specified shell
```

## apply

> apply all resources from state file only when there are changes

```sh
helmfile apply
```

## build

> Build all resources from state file

```sh
helmfile build
```

## cache

> cache management

```sh
helmfile cache
```

## deps

> Update charts based on their requirements

```sh
helmfile deps
```

## destroy

> Destroys and then purges releases

```sh
helmfile destroy
```

## diff

> diff releases defined in state file

```sh
helmfile diff --environment ENV --namespace NS --color -f helmfile.yaml --suppress-secrets
```

## fetch

> Fetch charts from state file

```sh
helmfile fetch
```

## help

> Help about any command

```sh
helmfile help
```

## init

> Initialize the helmfile, includes version checking and installation of helm and plug-ins

```sh
helmfile init
```

## lint

> Lint charts from state file (helm lint)

```sh
helmfile lint
```

## list

> List releases defined in state file

```sh
helmfile list
```

## repos

> Add chart repositories defined in state file

```sh
helmfile repos
```

```sh
helmfile show-dag     # prints table with 3 columns, GROUP, RELEASE, and DEPENDENCIES
helmfile status       # Retrieve status of releases in state file
helmfile sync         # Sync releases defined in state file
helmfile template     # Template releases defined in state file
helmfile test         # Test charts from state file (helm test)
helmfile version      # Print the CLI version
helmfile write-values # write values files for releases. Similar to `helmfile template`, write values files instead of manifests.
```

## see also

- [[helm]]
- [[terragrunt]]
- [[go-template]]

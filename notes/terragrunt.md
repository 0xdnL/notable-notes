---
tags: [iac]
title: terragrunt
created: '2023-09-15T07:56:46.974Z'
modified: '2023-09-15T07:58:31.971Z'
---

# terragrunt

> thin wrapper provides extra tools for keeping config DRY, working with multiple Terraform modules, and managing remote state

## install

```sh
brew install terragrunt
```

## usage

```sh
terragrunt run-all
terragrunt terragrunt-info
terragrunt validate-inputs
terragrunt graph-dependencies
terragrunt hclfmt
terragrunt aws-provider-patch
terragrunt render-json
terragrunt output-module-groups
```

## see also

- [[terraform]]

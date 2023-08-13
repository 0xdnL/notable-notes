---
tags: [iac]
title: terraform
created: '2019-07-30T06:19:49.078Z'
modified: '2023-08-13T08:03:55.315Z'
---

# terraform

> tool for building, changing, and versioning infrastructure safely and efficiently

## install

```sh
tfswitch 0.14.4
```

## environment variables

```sh
TF_LOG_PATH       #
TF_INPUT          #
TF_LOG            # TRACE, DEBUG, INFO, WARN or ERROR
TF_VAR_name       # e.g. "TF_VAR_region=us-west-1"

TF_LOG=DEBUG terraform apply &> log
```

## usage

```sh
terraform state -json | fx                                              # print whole state as json

terraform state list                                                    # check state

terraform state show 'module.path.data["name"] '                        # show state of resource

terraform state rm 'module.NAME'                                        # removes all associatd with module.Name

terraform state mv 'aws_vpc.ds-vpc' 'aws_vpc.ds_vpc'                    # rename resource
terraform state mv 'some_resource' 'module.app.some_resource'           # moves resource into module
terraform state mv 'module.app' 'module.parent.module.app'              # move module insid other module
terraform state mv -state-out=other.tfstate 'module.app' 'module.app'   # move module to other state

terraform state replace-provider 'registry.terraform.io/-/happycloud' 'terraform.example.com/awesomecorp/happycloud'  # after upgrade to 0.13

terraform state list | grep PROVIDER_RESOURCE | sed 's/"/\\"/g' | xargs -I {} terraform state rm '{}'

terraform 0.13upgrade .

terraform validate -json                  # json-flag for showing all warnings, and where
terraform validate -json | jq '.diagnostics[] | {detail: .detail, filename: .range.filename, start_line: .range.start.line}'
terraform validate -json | jq -r '.diagnostics[] | "\(.address): \(.detail)"'
terraform validate -json \
  | jq -r '[ del( .diagnostics[] | select( .detail | startswith( "Experimental features" ) ) ) | .diagnostics[] | { Detail:.detail, Address:.address, Filename:.range.filename, Line:.range.start.line } ] | ( .[0] | keys_unsorted | ( . , map( length*"-" ) ) ), .[] | map(.) | @tsv' \
  | column -ts $'\t'

terraform fmt -diff -check  main.tf       # check format configuration

terraform fmt -write main.tf              # format config

terraform graph | dot -Tsvg > graph.svg

terraform graph -draw-cycles -module-depth=2
  -type=plan-destroy        `# -type=[plan|plan-destroy|apply|validate|input|refresh]` \
  | dot -Tsvg > graph.svg    # generate a visual representation of either a configuration or execution plan

terraform console     # startes repl-like console
```



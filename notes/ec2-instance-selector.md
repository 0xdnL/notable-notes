---
tags: [cloud]
title: ec2-instance-selector
created: '2022-01-18T19:33:51.186Z'
modified: '2024-10-22T09:25:32.919Z'
---

# ec2-instance-selector

> recommends instance types based on resource criteria like vcpus and memory

## install

```sh
brew tap aws/tap
brew install ec2-instance-selector
```

## environment

```sh
AWS_PROFILE                     # select aws profile
```

## option

```sh
      --debug                   # prints debug log messages                                                     
      --max-results int         # maximum number of instance types that match your criteria to return (default 20)
  -o, --output string           # specify output format (table, table-wide, one-line, interactive)                                                              
      --profile string          # AWS CLI profile to use for credentials and config                                                                  
  -r, --region string           # AWS Region to use for API requests (NOTE: if not passed in, uses AWS SDK default precedence)
      --sort-by string          # specify field to sort by.(memory, gpus, etc.) or a JSON path to the appropriate instance type field (Ex: ".MemoryInfo.SizeInMiB") is acceptable. (default ".InstanceType")
      --sort-direction string   # specify direction to sort in (ascending, asc, descending, desc) (default "ascending")

-u, --usage-class CLASS         # CLASS: [spot|on-demand] 
```

## usage

```sh
ec2-instance-selector --service eks

ec2-instance-selector --memory 4 --vcpus 2 --cpu-architecture x86_64 -r REGION -o table

ec2-instance-selector --network-performance 100 --usage-class spot -r REGION

AWS_PROFILE='mfa' ec2-instance-selector \
  --region eu-central-1 \
  --vcpus 8 \
  --memory 16gb \
  --cpu-architecture x86_64 \
  --usage-class spot \
  --gpus 0 \
  --sort-by ".OndemandPricePerHour" \
  --output table-wide
```

## ec2.shop alternative

```sh
curl 'https://ec2.shop?region=us-west-2'
curl 'https://ec2.shop?region=us-west-2&filter=m4,m5,ssd'
curl 'https://ec2.shop' -H 'accept: json'
```

## see also

- [[aws]]
- [[curl]]

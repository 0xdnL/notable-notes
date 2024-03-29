---
tags: [Notebooks]
title: iac
created: '2019-07-30T06:19:49.081Z'
modified: '2022-10-17T10:55:16.675Z'
---

# iac

> infrastructure as code

## pets vs cattle

> If you view a server (whether metal, virtualized, or containerized) as inherently something that can be `destroyed and replaced at any time`, then it’s a member of the `herd`.
> If, however, you view a server (or a pair of servers attempting to appear as a single unit) as `indispensable`, then it’s a `pet`.


## providers

|       | chef          | puppet        | ansible       | saltstack     | cloudformation  | terraform   | 
|:--    |:--            |:--            |:--            |:--            |:--              |:--          | 
| code  | opensource    | opensource    | opensource    | opensource    | opensource      | opensource  |
| type  | config mgmt   | config mgmt   | config mgmt   | config mgmt   | orchestration   | orchestration |
| infra | mutable       | mutable       | mutable       | mutable       | immutable       | immutable   |
| lang  | procedural    | declarative   | procedural    | declarative   | declarative     | declarative |
| arch  | Client/Server | Client/Server | Client/Server | Client/Server |  Client-Only    | Client-Only |

## see also

- [[12 factor app]]
- [[gitops]]
- [[terraform]]
- [[aws cloudformation]]
- [cloudscaling.com/the-history-of-pets-vs-cattle/](http://cloudscaling.com/blog/cloud-computing/the-history-of-pets-vs-cattle/)
- [why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation](https://blog.gruntwork.io/why-we-use-terraform-and-not-chef-puppet-ansible-saltstack-or-cloudformation-7989dad2865c)

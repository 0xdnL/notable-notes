---
tags: [iac]
title: ansible-playbook
created: '2019-11-28T11:53:47.807Z'
modified: '2024-03-23T15:50:08.818Z'
---

# ansible-playbook

> runs ansible playbooks, executing the defined tasks on the targeted hosts.

## install

see [[ansible]]

## usage

```sh
ansible-playbook --syntax-check playbook.yml

ansible-playbook --list-hosts playbook.yml

ansible-playbook --list-tasks playbook.yml

ansible-playbook -i hosts ansible-bootstrap-ubuntu-16.04.yml    # bootstraps machine with python2
```

## see also

- [[ansible-inventory]]

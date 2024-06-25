---
tags: [iac]
title: ansible
created: '2019-07-30T06:19:27.514Z'
modified: '2024-03-23T15:50:29.602Z'
---

# ansible

> software provisioning, configuration management, and application-deployment tool enabling infrastructure as code

## install

```sh
virtualenv venv 
source venv/bin/activate
pip install ansible
```

[[pip]], [[virtualenv]]

## environment

```sh
ANSIBLE_HOST_KEY_CHECKING
```

## usage

```sh
ansible all -m ping -s                              # adhoc command

ansible all -m shell -a 'cat /etc/*release'         # adhoc command using shell string

ansible -i hosts all -m ping                        # uses local hosts file
```

## see also

- [[ansible-inventory]]
- [[ansible-playbook]]
- [[ssh]]
- [[terraform]], [[aws]] `cloudformation`

---
title: docker-compose.yaml
created: '2024-02-08T12:35:20.028Z'
modified: '2024-02-08T12:35:59.498Z'
---

# docker-compose.yaml

```yml
# compose file version 2 reference
ulimits:        # this is docker-compose only !
  memlock:
    soft: -1
    hard: -1

cap_add:
  - ALL

cap_drop:
  - NET_ADMIN
  - SYS_ADMIN
```

```yml
# compose file version 3 reference
cap_add:
  - ALL
cap_drop:
  - NET_ADMIN
  - SYS_ADMIN
```

[[capabilities]], [[ulimit]]

```yml
# terrafrom dev setup
version: '2.4'

services:
  terraform:
    build:
      context: .
      args:
        TAG: 0.12.6
    image: docker-registry/terraform:0.12.6
    tty: true
    stdin_open: true
    environment:
      TF_VAR_vsphere_server: ${vsphere_server}
      TF_VAR_vsphere_user: ${vsphere_user}
      TF_VAR_vsphere_password: ${vsphere_password}
    volumes:
    - ./:/opt/terraform/
    - /var/run/docker.sock:/var/run/docker.sock
```

## see also

- [[docker-compose]]
- [[Dockerfile]]
- [[kubectl]]

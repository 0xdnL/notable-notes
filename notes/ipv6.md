---
title: ipv6
created: '2024-11-16T07:51:51.309Z'
modified: '2024-11-16T08:07:12.199Z'
---

# ipv6


> ipv6 is a new version of the Internet Protocol, designed as the successor to [[ipv4]]

[RFC-4291: IP Version 6 Addressing Architecture](https://www.rfc-editor.org/rfc/rfc4291.html)
[RFC-8200: Internet Protocol, Version 6 (IPv6) Specification](https://www.rfc-editor.org/rfc/rfc8200.html)

[[cidr]]

```
  +--------------------------------------------------------------------+
  |                           128 bits                                 |
  +--------------------------------------------------------------------+
  |                          node address                              |
  +--------------------------------------------------------------------+
  |          64 bits                 |           64 bits               |
  +----------------------------------+---------------------------------+
  | global routingprefix | subnet ID |           interface ID          |
  +----------------------------------+---------------------------------+
```


## see also

- [[ip]], [[ipcalc]]
- [[iptables]]
- [[osi model]]
